---
title: "How should I convert a jpg figure into the pdf format?"
date: 2008-10-17
forum: General Help
---

### Post by subjugater on 2008-10-17
Is there any command can achieve this?

Thanks.

---

### Post by cmnorton on 2008-10-17
Print it. 

Ubuntu comes with a pdf printer by default. It's called cups-pdf. Have a look in /etc/cups/cups-pdf.conf.

---

### Post by KeyserSoze93 on 2008-10-17
ImageMagick allows you into convert various "image" formats, including pdf.

Install it and then run "convert whatever.jpg whatever.pdf"

---

### Post by mbeach on 2008-10-17
when you use that pdf printer cmnorton suggests, by default you'll find the output in /home/yoururser/PDF (as you'll see in the .conf file)

---

### Post by ichigo on 2008-10-17
> **mbeach said:**
> when you use that pdf printer cmnorton suggests, by default you'll find the output in /home/yoururser/PDF (as you'll see in the .conf file)

the pdf printer seems to be broken on Intrepid beta (Hope they fix it soon).

You could also try:
```
sam2p input.jpg PDF: output.jpg
```
(If sam2p isn't installed, you can get it via Synaptics)

---

