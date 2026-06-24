
<div align="center">
  <img src="https://i.ibb.co/1Y34BkpH/1000271428-removebg-preview.png" width="500">
</div> 

## $addContainer[ID;(Color;Spoiler)]

El **$addContainer** de Bot Designer For Discord (BDFD) tiene varias y muy interesantes funciones.

Podrías estar pensando, para qué usar el **$addContainer** si ya tenemos el **$description**. Ahí es donde muchos piensan que el **$addContainer** es solo una manera de hacer más complicado el hacer Embeds en BDFD de manera más larga y cansada, pero en parte tienes razón.

Si estás acostumbrad@ al estilo común de Discord y no te agradan las actualizaciones *(hay veces que si se pasan pero se deja de lado)* entonces esta información no te debería interesar hasta ahora.

---

## Características del $addContainer

- **$addContainer**
  - **ID:** El nombre o código que le pondrás al contenedor para que BDFD lo reconozca en el código.
  - **Color:** El color del contenedor (Embed) representado en colores hexadecimales (HEX).
  - **Spoiler:** Acepta `true`/`false`. Viene `false` como predeterminada. Si se pone `true`, el Embed saldrá marcado como Spoiler como si fuera una imagen.

<div align="center">
  <img src="https://i.ibb.co/PqgqLvQ/Picsart-26-05-16-13-45-37-838.png" width="500">
</div> 

---

## $addTextDisplay

El primer uso del **$addContainer** es el integrado de textos usando:

```
$addTextDisplay[Content;(Container/Section ID)]
```

- **$addTextDisplay**
  - **Content:** El contenido o texto que pondrán en el contenedor.
  - **(Container/Section ID):** Aquí va la ID del contenedor o la sección dentro del contenedor.

### Ejemplo básico

```
$nomention
$addContainer[id;#673ab7;false] $c[La opción final se puede dejar vacía]
$addTextDisplay[Texto del contenedor;id]
```

<div align="center">
  <img src="https://i.ibb.co/ym8Sv2Mh/Screenshot-20260516-135846-Discord.jpg" width="500">
</div> 

---

## $addSection y $addThumbnail

Para añadir imágenes/thumbnail al contenedor se usan **$addSection** y **$addThumbnail**.

> [!IMPORTANT]
> El **$addThumbnail** no admite añadirse directamente al contenedor; requiere una sección.

- **$addSection[ID;(Container ID)]**
  - **ID:** La ID de la sección.
  - **Container ID:** La ID del contenedor donde se establecerá la sección.

- **$addThumbnail[Image URL;Image description;Spoiler;Section ID]**
  - **Image URL:** URL de la imagen que se pondrá de Thumbnail.
  - **Image description:** Descripción de la imagen de Thumbnail.
  - **Spoiler:** Valores `true`/`false`. Si se pone `true`, la imagen se marcará como Spoiler.
  - **Section ID:** La ID de la sección creada con `$addSection`.
> [!WARNING]
>⚠️ Al usar **$addSection** es **obligatorio** añadir al menos un texto con **$addTextDisplay**, de lo contrario aparecerá el error: `Section needs at least 1 Text Display component — use $addTextDisplay to add content`

### Ejemplo con Thumbnail

```
$nomention
$addContainer[id-contenedor;#673ab7;false]
$addSection[id-seccion;id-contenedor]
$addTextDisplay[Texto del contenedor;id-seccion]
$addThumbnail[$authorAvatar;Descripcion de la imagen;false;id-seccion]
```

<div align="center">
  <img src="https://i.ibb.co/x8dNpGbW/Screenshot-20260516-142642-Discord.jpg" width="500">
</div> 

---

## $addMediaGallery y $addMediaGalleryItem

Para añadir imágenes completas (no thumbnail) se usan **$addMediaGallery** y **$addMediaGalleryItem**.

- **$addMediaGallery[ID;(Container ID)]**
  - **ID:** La ID con la que será reconocida la galería.
  - **Container ID:** La ID del contenedor (no requiere sección).

- **$addMediaGalleryItem[Media URL;Description;Spoiler;Gallery ID]**
  - **Media URL:** URL de la imagen que será añadida al contenedor.
  - **Description:** Descripción de la imagen.
  - **Spoiler:** Valores `true`/`false`. Si se pone `true`, la imagen saldrá marcada como Spoiler.
  - **Gallery ID:** La ID definida en `$addMediaGallery`.

### Ejemplo con imagen

```
$nomention
$addContainer[id-contenedor;#673ab7;false]
$addMediaGallery[id-galeria;id-contenedor]
$addMediaGalleryItem[$authorAvatar;Descripcion de la imagen;false;id-galeria]
```
<div align="center">
  <img src="https://i.ibb.co/sG1btN0/Screenshot-20260516-150126-Discord.jpg" width="500">
</div> 
---

## Componentes V2 de Discord

La ventaja principal del **$addContainer** es el acceso anticipado a los **componentes V2 de Discord**: botones y menús interactivos *dentro* del Embed, algo imposible con `$description`.

### $addActionRow

- **$addActionRow[ID;(Container ID)]**
  - **ID:** La ID del ActionRow.
  - **Container ID:** La ID del contenedor donde será colocado el ActionRow.

A diferencia de `$addSection`, `$addActionRow` permite tener **más de uno** dentro del mismo contenedor.

---

### $addButtonCV2

```
$addButtonCV2[Button ID/URL;Label;Style;Disabled;Emoji;Action Row ID / Section ID]
```

- **Button ID/URL:** ID del botón para interactuar con `$onInteraction`, o URL si es un botón de tipo link.
- **Label:** Nombre visible del botón.
- **Style:** Color del botón — `primary` (azul), `success` (verde), `danger` (rojo), `secondary` (gris). Si se usa URL, debe ser `link`.
- **Disabled:** `true`/`false`. Si es `true`, el botón no será interactivo.
- **Emoji:** Emoji opcional del botón (emojis del servidor con su nombre exacto, ej: `:emoji_25:`).
- **Action Row ID / Section ID:** ID del ActionRow o Sección donde se colocará el botón.

### Ejemplo con botón CV2

```
$nomention
$addContainer[id-contenedor;#673ab7;false]
$addTextDisplay[Boton CV2 de Discord en BDFD;id-contenedor]
$addActionRow[id-actionRow;id-contenedor]
$addButtonCV2[https://youtu.be/LWEsL2osOa4?is=X4grJMCw005q6PYJ;Boton CV2;link;false;<:jejeje:1432509409463894208>;id-actionRow]
```
<div align="center">
  <img src="https://i.ibb.co/bjpmH5Yg/Screenshot-20260516-175159-Discord.jpg" width="500">
</div> 
---

## $addStringSelect y $addStringSelectOption

Para añadir menús desplegables interactivos dentro del Embed.

### $addStringSelect

```
$addStringSelect[Select Menu ID;Placeholder;Min Values;Max Values;Disabled;Action Row ID]
```

- **Select Menu ID:** ID del menú desplegable.
- **Placeholder:** Nombre/texto visible del menú.
- **Min Values:** Mínimo de opciones a elegir.
- **Max Values:** Máximo de opciones a elegir.
- **Disabled:** `true`/`false`. Si es `true`, el menú no será interactivo.
- **Action Row ID:** ID del ActionRow (no usa sección).

### $addStringSelectOption

```
$addStringSelectOption[Label;Value;Description;Emoji;Default;Select Menu ID]
```

- **Label:** Nombre de la opción.
- **Value:** ID de la opción para interactuar con `$onInteraction`.
- **Description:** Texto descriptivo que aparece debajo del nombre de la opción.
- **Emoji:** Emoji opcional (ej: `:emoji_25:`).
- **Default:** `true`/`false`. Si es `true`, la opción será seleccionada automáticamente.
- **Select Menu ID:** ID del menú donde se añade la opción.

### Ejemplo con menú desplegable

```
$nomention
$addContainer[id-contenedor;#673ab7;false]
$addTextDisplay[Menu desplegable CV2 de Discord en BDFD;id-contenedor]
$addActionRow[id-actionRow;id-contenedor]
$addStringSelect[id-menu;Menu CV2 dentro del Embed;1;1;false;id-actionRow]
$addStringSelectOption[Opcion 1 CV2;id-1;Esta es la opcion 1;;false;id-menu]
$addStringSelectOption[Opcion 2 CV2;id-2;Esta es la opcion 2;;false;id-menu]
```
<div align="center">
  <img src="https://i.ibb.co/F48YDRkh/Screenshot-20260516-181551-Discord.jpg" width="500">
</div> 

---

*Atentamente: MPG*

Co autor **TwisSpark**

<sup>Dar las gracias al equipo Sparky :D</sup>
