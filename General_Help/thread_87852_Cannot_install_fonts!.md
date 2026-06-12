---
title: "Cannot install fonts!"
date: 2005-11-09
forum: General Help
---

### Post by ramdisc on 2005-11-09
I am using System Settings > Font Installer to install a font.  I click on Add Fonts...   Select the font, click on Apply.  But it doesn't work; the new font doesn't show up in any options.

---

### Post by mlomker on 2005-11-09
Is it a font that I can download and give it a try?

---

### Post by ramdisc on 2005-11-09
I forgot where I got the font from.  But its called Smooth.  Sometimes called Artwiz Smooth.

When installed it should show up as either: Smooth, Artwiz Smooth, or Misc Smooth.  Sometimes Misc or Artwiz are in square brackets.  But I didn't find any of them in the list.

---

### Post by hazza96 on 2005-11-10
I am trying to install the ones you can download from here: [http://www.barcodesinc.com/free-barcode-font/](http://www.barcodesinc.com/free-barcode-font/)

---

### Post by hazza96 on 2005-11-10
Ah bugger, I didn't see that I was in the Kubuntu section.

---

### Post by mlomker on 2005-11-10
[QUOTE=ramdisc]I forgot where I got the font from.  But its called Smooth.  Sometimes called Artwiz Smooth.
[/QUOTE]

I searched Google and couldn't find a copy, otherwise I'd give it a try and see if it worked on my machine.

---

### Post by rcerreto on 2005-11-10
Smooth is a bitmapped font which I use frequently. Bitmapped fonts are not enabled by default.

**sudo dpkg-reconfigure fontconfig**

then answer yes to the question "Enable bitmapped fonts by default?"

Can't remember whether you need to logout and to restart X before having the bitmapped fonts available

---

### Post by ramdisc on 2005-11-10
Thank you so much, Rcerreto!  Thanks everyone else for trying to help.

I couldn't live without this fixed font.  And I will die with it too; I will take it to the grave with me.  By means of engraving it onto my gravestone. :D

---

