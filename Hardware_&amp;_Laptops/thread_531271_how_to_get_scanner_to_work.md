---
title: "how to get scanner to work?"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by Linux_noob1 on 2007-08-21
I have a artec e48+ scanner
The problem is it wont work. I tried opening Xsane but it didn't recognize it. :( I can't get kubuntu (feisty) to see it.
Is there any way to get this scanner to work? And would it be hard?
  Has anyone gotten a scanner like this to work on ubuntu/kubuntu?

---

### Post by scrooge_74 on 2007-08-21
You have to check if the scanner is supported under linux, check in [http://www.sane-project.org/](http://www.sane-project.org/)

If your scanner is not supported you are out of luck with it

EDIT: I checked the website and the E48U is well supported, is the same as yours?

---

### Post by l33t_3lv3n_g33k on 2007-08-21
I have and HP scanner that was not being recognized by xsane when I first plugged it in. I had to load a driver and then change the permissions on the device. I'll have to see if I can find that thread again (It's somewhere on the ubuntu forums...) for a general idea of what you may need to do. 
 
For starters, you can run 'lsusb' (assuming your scanner connects via usb) and see if ubuntu is recognizing it or not.
 
Post the output from lsusb here.

---

### Post by vexorian on 2007-08-21
in the extreme case the scanner is unsupported, if it is an USB you can actually use a virtual machine to use it, I now use my windows XP virtual machine when I need the scanner.

---

