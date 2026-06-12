---
title: "I can't view SVG files in Firefox"
date: 2008-09-25
forum: General Help
---

### Post by gleble on 2008-09-25
I can't view SVG files in Firefox. It just displays the text file at best, sometimes it can't find the file. Does anyone know why?

---

### Post by nikgare on 2008-09-25
Is this all SVG files, or just spoecific ones?

Can you give the url of a couple that fail to display properly in firefox.

There are lots of examples available here:
[http://www.w3schools.com/svg/svg_examples.asp](http://www.w3schools.com/svg/svg_examples.asp)

Do these fail to display as well?

---

### Post by silverglade00 on 2008-09-25
If it helps, none of the files under SVG Misc. will display on my computer. The rest work fine. It seems to be the ones with animation that do not work.

---

### Post by gleble on 2008-09-25
It seems to be animation that is the problem now (I installed adobesvg) therefore the w3c examples involving fading, changing colour etc don't work

---

### Post by gleble on 2008-09-25
As I'm getting little response I assume Firefox cannot display animated SVGs
Does anyone know a package (not INK) that can?

---

### Post by gleble on 2008-09-26
Doesn't anyone know how to display animated svg files

---

### Post by kokkus on 2008-09-26
1. Open about:config, add new "svg.enabled" type: boolsk, value: true
2. Add new "network.protocol-handler.app.svg" type: strang, value: The command to the program you normaly use to open svg files.

Good luck:)

---

### Post by gleble on 2008-09-26
I've got "svg.enabled" type: boolean, value: true
How do I change it?

---

