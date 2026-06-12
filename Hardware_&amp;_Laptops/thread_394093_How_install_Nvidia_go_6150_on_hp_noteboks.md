---
title: "How install Nvidia go 6150 on hp noteboks?"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by mchiareli on 2007-03-26
Hi,...

i have a hp pavillion latop, model dv6120br (brazilian model).

the graphic card do not works very well, beryl is veryl slow and the windows sometimes crashes..

the option menu - restricted drivers manager - say "you don't have a restricted drivers on pc" ...

i install the ubuntu feisty because , on the ubuntu edgy my graphic card was total ****.

now im using the "nv" diver and quality image is good, but beryl is a total ****.., and i do not obtain the nvidia driver.... 

How to fix this problem?

thanks....

---

### Post by Waappu on 2007-03-26
Hi

Use envy to install driver and configure xorg.conf
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by mchiareli on 2007-03-26
> **Waappu said:**
> Hi

Use envy to install driver and configure xorg.conf
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

but... envy works on beta version: Ubuntu 7.04 Feisty?

---

### Post by s0cket on 2007-03-26
All you need is build essentials and the kernal headers to install from the Nvidia offical package.

---

### Post by Waappu on 2007-03-26
> **mchiareli said:**
> but... envy works on beta version: Ubuntu 7.04 Feisty?

Hi

I don't know, it seems it not. I didn't know you run Feisty.

Edit.
> i install the ubuntu feisty
Sorry my fault. Didn't read your post careful. I'm very sorry

---

### Post by mchiareli on 2007-03-26
> Sorry my fault. Didn't read your post careful. I'm very sorry

no problems...

probably it is my fault, my english is bad.... very bad...

---

### Post by Waappu on 2007-03-26
> **mchiareli said:**
> no problems...

probably it is my fault, my english is bad.... very bad...

Hi

You noticed right away that envy isn't ready for Feisty.
So no problem there. I didn't read what you say.

I hope this help you
[http://ubuntuforums.org/showthread.php?t=357501&highlight=feisty+nvidia+beryl](http://ubuntuforums.org/showthread.php?t=357501&highlight=feisty+nvidia+beryl)

---

### Post by mchiareli on 2007-03-29
hello...

dont works yet...

beryl is small......very small

---

### Post by Slim Odds on 2007-03-29
> **mchiareli said:**
> 
now im using the "nv" diver and quality image is good, but beryl is a total ****.., and i do not obtain the nvidia driver.... 

How to fix this problem?

thanks....

Beryl will NOT work with the "nv" driver. It is a 2D only driver. You really need to get the drivers from NVidia. They are not hard to install. Just download, set to executable (chmod +x) and run it.

---

### Post by mchiareli on 2007-03-31
> **Slim Odds said:**
> Beryl will NOT work with the "nv" driver. It is a 2D only driver. You really need to get the drivers from NVidia. They are not hard to install. Just download, set to executable (chmod +x) and run it.

nvidia driver is horrivel, is worse that driver nv

---

