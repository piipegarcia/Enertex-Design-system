# Design System – Front-end CSS

Autor / Creador: Felipe Garcia  
Versión: 1.0.0

Este Design System proporciona una capa de estilos opinados para una tienda basada en WordPress/Elementor/WooCommerce. Está organizado por capas (tokens → base → layout → componentes → utilidades) para que puedas escalar y personalizar con seguridad.

## 1) Estructura de archivos

./variables.css   → Tokens de diseño (colores, espaciados, radios, tamaños)  
./base.css        → Reset básico, tipografía global y elementos HTML base  
./layout.css      → Grid de 12 columnas y helpers de layout  
./components.css  → Componentes (botones, cards) + overrides de e-commerce  
./utilities.css   → Clases utilitarias (márgenes, paddings, gaps, fondos…)  
./main.css        → Punto de entrada que importa todo en el orden correcto

> Carga `main.css` para importar todo el sistema de una vez.

## 2) Instalación / Carga

### Opción A – HTML (estático)
<link rel="stylesheet" href="/ruta/a/main.css" />

### Opción B – WordPress (functions.php)
wp_enqueue_style(
  'design-system',
  get_stylesheet_directory_uri() . '/css/main.css',
  [],
  '1.0.0'
);

## 3) Tokens (variables CSS)

Todos los “dials” del sistema están en `variables.css`:
- Paleta: --color-primary-*, --color-white, --color-gray-*, etc.
- Espaciado: --spacing-* / --padding-* / --margin-*
- Radios: --border-radius-*
- Tamaños fluidos: --size-*

Personaliza con un override cargado DESPUÉS:
:root{
  --color-primary-600: #0751a8;
  --border-radius-md: 0.75rem;
}

## 4) Base
- Reset suave (box-sizing, márgenes a 0, etc.).
- Tipografía global y elementos HTML normalizados.
- Ajustes de contenedores principales y breadcrumbs.

## 5) Layout
Grid de 12 columnas con helpers `.col-*`:
.grid { display:grid; grid-template-columns:repeat(12,1fr); gap:var(--spacing-md); }

## 6) Componentes (extracto)
- Botones: `.btn`, `.btn-primary`
- Cards: `.card`, alturas utilitarias
- Tienda (Woo/Elementor/Jet*): product cards, barra de búsqueda, galería, checkout/cart, reviews, bundles…

## 7) Utilidades
Espaciado (`.p-*`, `.m-*`, `.py-*`, `.px-*`), gaps (`.row-gap-*`, `.col-gap-*`), fondos (`.bg-*`), radios (`.br-*`), estilos de enlace, outline hover, etc.

## 8) Convenciones
- Añade/ajusta tokens en `variables.css`; no edites core si no es necesario.
- Componentes con prefijos por contexto (`ProductSingle_*`, `Header*`, etc.).
- Encapsula overrides de plugins dentro de contenedores para evitar fugas.

## 9) Accesibilidad
- Tipos y tamaños pensados para legibilidad.
- Estados `:hover` visibles; añade `:focus-visible` si navegas por teclado.

## 10) Rendimiento
- Carga un único `main.css` (reduce solicitudes).
- Minifica tus overrides y evita @import en runtime.

## 11) Compatibilidad
- Requiere navegadores con soporte de **CSS Variables**.
- IE11 no soportado.

## 12) Ejemplos rápidos

Card con CTA
<div class="card p-md s-sm">
  <h3 class="m-0">Título</h3>
  <p class="mb-sm">Texto descriptivo…</p>
  <button class="btn btn-primary">Acción</button>
</div>

Product grid
<div class="grid">
  <article class="col-4 card p-md">Producto 1</article>
  <article class="col-4 card p-md">Producto 2</article>
  <article class="col-4 card p-md">Producto 3</article>
</div>

Barra JetSearch (envoltorio)
<div class="search-bar">
  <!-- Widget JetSearch -->
</div>

## 13) Mantenimiento
- Nuevos componentes → `components.css` + documentación aquí.
- Nuevos tokens → `variables.css`.
- Valida cambios en staging (plantillas Woo/Elementor/Jet*).

## 14) Licencia (MIT – abierta para uso privado y comercial)

Copyright (c) 2025 Felipe Garcia — https://felipegarcia.com

Se concede permiso, de manera gratuita, a cualquier persona que obtenga una copia de este software y de los archivos de documentación asociados (el “Software”), para usar el Software sin restricción, incluyendo sin limitación los derechos a usar, copiar, modificar, fusionar, publicar, distribuir, sublicenciar y/o vender copias del Software, y a permitir a las personas a las que se les proporcione el Software que lo hagan, sujeto a las siguientes condiciones:

El aviso de copyright anterior y este aviso de permiso se incluirán en todas las copias o partes sustanciales del Software.

EL SOFTWARE SE PROPORCIONA “TAL CUAL”, SIN GARANTÍA DE NINGÚN TIPO, EXPRESA O IMPLÍCITA, INCLUYENDO PERO NO LIMITADO A GARANTÍAS DE COMERCIALIZACIÓN, IDONEIDAD PARA UN PROPÓSITO PARTICULAR Y NO INFRACCIÓN. EN NINGÚN CASO LOS AUTORES O TITULARES DEL COPYRIGHT SERÁN RESPONSABLES DE NINGUNA RECLAMACIÓN, DAÑO U OTRA RESPONSABILIDAD, YA SEA EN UNA ACCIÓN CONTRACTUAL, AGRAVIO O DE OTRO TIPO, QUE SURJA DE, O EN CONEXIÓN CON EL SOFTWARE O EL USO U OTRO TIPO DE ACCIONES EN EL SOFTWARE.
