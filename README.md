# TeslAI

Aplicación educativa estática sobre física e inteligencia artificial aplicada al tráfico. Está hecha con HTML, CSS y JavaScript sin servidor, fuentes externas ni dependencias de compilación, para que pueda publicarse directamente en GitHub Pages.

## Publicación estática en GitHub Pages

1. Copia el contenido de esta carpeta a la raíz de un repositorio o publícala como carpeta del repositorio.
2. En GitHub, abre **Settings → Pages**.
3. Selecciona **Deploy from a branch**, elige la rama y la carpeta que contiene `index.html` (raíz o `/docs`).
4. Guarda y espera a que GitHub Pages publique el sitio.

Esta opción publica la experiencia educativa estática. GitHub Pages no ejecuta la función del asistente incluida en `functions/api/ask.js`, así que el panel conserva el modo local y ofrece continuar en Microsoft Copilot cuando no haya backend.

## Publicar con IA y búsqueda web

Para activar respuestas variadas dentro del panel, publica esta carpeta como proyecto de **Cloudflare Pages con Git integration**. Cloudflare Pages Functions detecta automáticamente la ruta `/api/ask` desde la carpeta `functions/`.

1. Sube el contenido completo de `outputs/teslai` a la raíz de un repositorio GitHub.
2. En Cloudflare, crea un proyecto Pages desde **Workers & Pages → Create application → Pages → Connect to Git** y elige ese repositorio.
3. No uses un comando de compilación. Como directorio de salida usa `.` (la raíz del repositorio).
4. En el proyecto, abre **Settings → Variables and Secrets** y añade `OPENAI_API_KEY` como secreto cifrado. No lo pongas en `app.js`, en GitHub ni en un archivo público.
5. Opcionalmente, establece `OPENAI_MODEL` como variable de texto si quieres cambiar el modelo por defecto (`gpt-6-astra`).
6. Vuelve a desplegar. La URL `*.pages.dev` que entrega Cloudflare será accesible desde teléfono, tableta y computadora.

El backend usa la Responses API y la herramienta de búsqueda web. La API de OpenAI se factura por separado de una suscripción de ChatGPT; revisa límites de uso y costes de tu cuenta antes de activarlo. La función limita el tamaño de las preguntas, no guarda el estado de la respuesta en el proveedor y aplica una pausa breve entre peticiones por IP. Para un despliegue público, añade también una regla de límite de solicitudes en Cloudflare.

Si todavía no configuras el backend, el chat responde con su base local y ofrece abrir Microsoft Copilot para continuar externamente.

Los recursos visuales originales se encuentran en `images/teslai-idle.png` y `images/teslai-talking.png`. El progreso se guarda en LocalStorage del navegador.

## Contenido

- Bienvenida interactiva y navegación guiada o libre.
- Siete módulos con conceptos, ejemplos, fórmulas y preguntas con retroalimentación.
- Cuatro simulaciones editables, incluida una intersección con fases seguras por eje.
- Chat local basado en palabras clave y contexto del módulo.
- Bibliografía con enlaces a publicaciones y fuentes técnicas.

Las simulaciones son modelos didácticos, no predicciones calibradas para operación vial real.
