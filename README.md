# Repair Academy v2

Guías de reparación de iPhone en español, con la foto de cada paso, herramientas, piezas y modo paso a paso. Es una página estática (`index.html`) que consulta la API pública de iFixit bajo demanda; no almacena ni replica su biblioteca.

## Cómo funciona

- **Catálogo:** lee las subcategorías de `iPhone` (`/wikis/CATEGORY/iPhone`) y carga la imagen y el número de guías de cada modelo solo cuando la tarjeta es visible.
- **Modelo:** lee `/wikis/CATEGORY/{modelo}`. Las guías se clasifican por pieza y tipo. Solo se muestran como principales las que nombran el modelo exacto («iPhone 12» no acepta «iPhone 12 Pro»); el resto va a una sección aparte con aviso de compatibilidad.
- **Guía:** pide `/guides/{id}?langid=es` y, si no hay traducción con pasos, usa la versión original y lo indica.
- **Fotos:** cada paso usa solo su propio `media.data[]`. Si un paso no tiene foto, se dice, y nunca se reutiliza la portada ni la imagen de otro paso.
- **Seguridad:** el HTML de la API pasa por un saneador con lista blanca; los enlaces externos llevan `noopener noreferrer`.
- **Diagnóstico:** si una guía llega con pasos pero sin ninguna imagen, se muestra un bloque desplegable con las claves recibidas, para corregir el formato rápidamente.

## Publicar

1. En el repositorio: **Settings → Pages → Deploy from a branch → `main` / root**.
2. Abre la URL que GitHub muestre.

También funciona abriendo `index.html` desde cualquier servidor estático.

## Licencia y límites

El contenido de iFixit está bajo CC BY-NC-SA 3.0: uso no comercial, con atribución y la misma licencia. Para un uso comercial hay que pedir permiso a iFixit. Ver `NOTICE.md`.

## Estado de la verificación

El código se escribió contra el formato documentado de la API v2.0 y se programa de forma defensiva (varios nombres de campo posibles). No se pudo probar en un navegador contra la API en vivo al crearlo, así que la primera ejecución real es la prueba. Si algo falla, abre un issue con la guía y el bloque de diagnóstico.
