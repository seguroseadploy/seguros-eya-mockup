# Mockup — Seguros E&A

Maqueta estática del sitio de **Seguros E&A**, correduría de seguros en Guatemala.
Se publica con GitHub Pages para poder mandar un enlace y que se vea el diseño sin
levantar nada.

**Esto no es el sitio.** El sitio es un tema y un plugin de WordPress —PHP— y vive
en un repositorio privado aparte. GitHub Pages sirve archivos estáticos y no
ejecuta PHP, así que lo que hay acá son cinco pantallas dibujadas a mano con los
mismos valores que el tema: las mismas pilas de tipografía, los mismos colores,
los mismos radios y espaciados.

## Las vistas

| Archivo | Medida | Qué es |
|---|---|---|
| `index.html` | fluida | Índice, con las notas de qué falta cargar |
| `portada.html` | 1280 px | La portada completa, de la cabecera al pie |
| `movil.html` | 390 × 844 px | El pliegue en un teléfono |
| `oscuro.html` | 1280 px | El modo oscuro, con su propia paleta |
| `cotizador.html` | 780 px | El cotizador de tres pasos, **funcionando** |
| `ficha.html` | 1280 px | La página de un ramo (Automóvil de ejemplo) |

El cotizador valida, arma el resumen y muestra la confirmación, pero **no envía
nada a ninguna parte**: no hay servidor detrás. La validación es la misma que
corre en el plugin —nombre de dos caracteres o más, teléfono de ocho o más— para
que lo que se ve acá sea lo que va a pasar de verdad.

## De dónde salen estos archivos

Las pantallas se diseñaron primero como mesas de trabajo en un lienzo de diseño,
en formato `.dc.html`. Ese formato envuelve el contenido en `<x-dc>`, mete los
estilos base en `<helmet>` y depende de un `support.js` que solo existe dentro del
editor, así que un navegador suelto no entiende nada de eso.

Cuatro de las cinco se convirtieron a HTML plano de forma mecánica: los estilos
del `<helmet>` pasaron al `<head>`, los envoltorios desaparecieron y el bloque de
lógica del editor se descartó. `cotizador.html` no: ahí la lógica vivía en
`renderVals()` con `{{huecos}}` y `<sc-if>`, así que se reescribió en JavaScript
normal.

## Tipografía y color

```
Titulares   Iowan Old Style → Palatino Linotype → Palatino → Book Antiqua → Georgia
Cuerpo      Arial → Helvetica Neue → Segoe UI → Roboto → Liberation Sans

Azul        #12376b   marca
Ámbar       #e8a020   acción
Verde       #1f9d55   confirmación
Rojo        #c62828   error  (5.6:1 sobre blanco)
```

Sin fuentes web y sin recursos externos: las mismas dos pilas que declara el
tema, resueltas por el sistema. En Windows los titulares caen en Palatino
Linotype; en el resto, en Georgia.

## Lo que falta cargar

Los datos entre corchetes —`[TELÉFONO]`, `[WHATSAPP]`, `[CORREO]`— son ajustes
que en el tema arrancan vacíos a propósito y se llenan desde el personalizador de
WordPress. Faltan además el logo real, la dirección física, la cita atribuida a
Einstein y los textos de «Quiénes somos».

Aliados y Testimonios no aparecen porque no hay contenido publicado. El tema
saltea la sección entera en vez de dejar un hueco.
