![Keepcoding](keepcoding.png)

# 🤖 **Práctica - Automatización de Respuestas a Solicitudes de Devolución** 📬

### ✍️ **Author:** Mirellys Arteta Davila

El objetivo de esta práctica era automatizar la gestión de respuesta a emails de devolución recibidos por la empresa ficticia "Componentes Intergalácticos Industriales S.A." (CII).

## 💡 Objetivo

Leer un email de cliente, extraer la información importante (número de pedido, nombre, motivo de contacto, etc.), evaluar si la devolución se acepta o no según ciertas reglas, y generar automáticamente una respuesta formal.

## 🔁 Flujo implementado

He construido un flujo de 3 pasos utilizando herramientas vistas en clase:

1. **Entrada**: Espero un email en texto libre.
2. **Procesamiento**: Mediante `StructuredOutputParser`extraigo los datos importantes, para analizar el motivo del email y decidir si la devolución es válida.
3. **Salida**: Genero una respuesta automática adaptada al caso, ya sea aceptando o rechazando la solicitud, con un tono formal y claro.

Todo está encapsulado en la función a modo de pipeline `process_email(...)` que permite ejecutar el flujo completo a partir de un email de entrada.

## 🔧 Herramientas

- Variables de entorno (`.env`) con `dotenv` para proteger la API key.
- `ChatOpenAI` para usar el modelo GPT-4o.
- `ChatPromptTemplate` para construir los prompts.
- `ResponseSchema` y `StructuredOutputParser` para extraer información estructurada.
- `invoke()` para interactuar con el llm.

## 🧾 Justificación de los prompts

- El primer prompt está diseñado para guiar al modelo a extraer campos clave del email, usando una lista clara y concreta con instrucciones de formato (`format_instructions`) para que el parser pueda interpretarlo.
- El segundo prompt genera la respuesta formal. Incluye condicionales en lenguaje natural para que el modelo sepa cuándo aceptar o rechazar la solicitud, basándose en el motivo extraído previamente.

## ⚖️ Criterios para aceptar o rechazar devoluciones

Se siguieron las condiciones dadas en el enunciado:
- **Aceptar**: Defecto de fabricación, error en el suministro, producto incompleto.
- **Rechazar**: Daño durante transporte, manipulación indebida, fuera de plazo.

## 🧪 Ejecución

El proyecto está preparado para ejecutarse en Google Colab con un email de ejemplo para ser rechazado y otro aceptado. Solo es necesario crear un archivo `.env` con la variable `OPENAI_API_KEY`.

---
