---
title: "Hotkeys on Acer 2200"
date: 2007-06-23
forum: Hardware &amp; Laptops
---

### Post by nirpius on 2007-06-23
I've got a new laptop and at the top are 4 buttons which I assume I can set to do different tasks. One has an envelope (email I suppose) one a picture of saturn, one an e (maybe internet) and one a p (presumably some custom program). I am running the latest version of Ubuntu (Feisty I think).

I don't know how to set these to do things.

I was looking on Sourcefourge and I found something called Acer Hotkey driver for Linux from [http://sourceforge.net/projects/acerhk/](http://sourceforge.net/projects/acerhk/) I downloaded the Tarball and unpackaged that then looked at the Install file and nearly cried. I honestly have no idea what it's talking about so I tried just running the makefile and that said error.

I've now realised I need to add the 'location of [my] kernel build tree' using Gedit I assume in the Make file where it says KERNELSRC but I don't know where to find that location or what it means.

Does anyone know? Or, even better, does anyone know an easier way to sort this?

Cheers

Oh yeah, in case you haven't noticed I'm a Ubuntu, Terminal and Programming noob so please keep it simple if possible

Cheers

---

### Post by Steveway on 2007-06-23
3v1n0 has it in his repository: [http://download.tuxfamily.org/3v1deb/index.html](http://download.tuxfamily.org/3v1deb/index.html)

---

### Post by nirpius on 2007-06-23
Thanks, I installed that but it still won't recognise the 4 keys at the top.

Does anyone know hwo to use the 4 keys at the top on an Acer? Or how to use the scroll button under the touchpad?

---

### Post by Steveway on 2007-06-24
Have you tried xev to see if there is a response to these keys?
Mine work. I have an Aspire 1363LM.

---

### Post by AJB2K3 on 2007-07-22
DO > sudo modprobe acerhk 
After install to create nodes but after that im lost.

---

