---
title: "Changed my icon theme, now no thumbnails are shown for text files!"
date: 2008-10-07
forum: General Help
---

### Post by Fixman on 2008-10-07
I currently changed my icon theme to the gTango theme, but I recently realized that no thumbnails with their text are shown for text files! Is there any way to solve this?

---

### Post by Fixman on 2008-10-07
help!

---

### Post by Soupcan on 2008-10-07
I've never had thumbnails for text documents? I am also interested in a solution/download to make this happen.

---

### Post by Fixman on 2008-10-08
So, can someone help me?

---

### Post by jpfle on 2008-11-20
I'm very interested too by this. Since I've changed in Gnome my icons theme for Oxygen, I've lost text files preview.

---

### Post by Andreas1 on 2008-11-21
use of this feature has to be specified by the icon theme you are using. for example, the default gnome icon theme has it:

in /usr/share/icons/gnome/scalable/mimetypes i found a text-x-preview.svg image file AND a text-x-preview**.icon** file that says
```
[Icon Data]
EmbeddedTextRectangle=180,100,680,900

```

i believe that is it. so you can either include this in your preferred icon theme or delete the text-whatever-icon from your preferred icon theme so it falls back on gnome icon theme.

---

### Post by Fixman on 2008-11-22
> **Andreas1 said:**
> use of this feature has to be specified by the icon theme you are using. for example, the default gnome icon theme has it:

in /usr/share/icons/gnome/scalable/mimetypes i found a text-x-preview.svg image file AND a text-x-preview**.icon** file that says
```
[Icon Data]
EmbeddedTextRectangle=180,100,680,900

```

i believe that is it. so you can either include this in your preferred icon theme or delete the text-whatever-icon from your preferred icon theme so it falls back on gnome icon theme.

I copied both text-x-preview.svg and text-x-preview.icon from /usr/share/icons/gnome/scalable/mimetipes to ~/.icons/gTango/scalable/mimetyoes with no result.

---

### Post by jpfle on 2009-01-24
> **Fixman said:**
> I copied both text-x-preview.svg and text-x-preview.icon from /usr/share/icons/gnome/scalable/mimetipes to ~/.icons/gTango/scalable/mimetyoes with no result.

Idem.

---

