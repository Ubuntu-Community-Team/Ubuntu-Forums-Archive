---
title: "Kernel i386 or kernel i686"
date: 2005-11-10
forum: General Help
---

### Post by Drifter on 2005-11-10
My computer is running an Athlon xp 3200+ processor which kernel should I be using.  I now have 2.6.12 i386.  If it would help to use the other one how do I install it rather than compiling.

---

### Post by teaker1s on 2005-11-10
synaptic 
kernel-image

[http://www.ubuntuforums.org/showthread.php?t=85917]("http://www.ubuntuforums.org/showthread.php?t=85917")

---

### Post by BoyOfDestiny on 2005-11-10
[QUOTE=Drifter]My computer is running an Athlon xp 3200+ processor which kernel should I be using.  I now have 2.6.12 i386.  If it would help to use the other one how do I install it rather than compiling.[/QUOTE]

I think you'd want the k7 kernel :)

Fire up Synaptic (System->Administration)

Unlike the post above mine, I search for linux-image (or just image). Scroll a bit and you'll see the one you have installed...a little below will be i686, k7, smp etc.

Choose k7, apply then reboot. Grub should boot it, if all goes well u can remove the i386 kernel (safer to reboot and test before removing it...Although I've done it a couple of times anyway =) )

---

### Post by Sutekh on 2005-11-10
The AMD Athlon XP is part of the K7 family of AMD processors, so I'd suggest that the k7 kernel is best suited for your CPU.

Synaptic has what you need, no need for compiling, and GRUB will be updated for you.  In Synaptic it will be in "Base System".

Ed: Like BoyofDestiny said

---

### Post by Drifter on 2005-11-10
O.K. so which k7 do I pick in snaptic there is more than one.

---

### Post by RAOF on 2005-11-10
You want the (meta)package "linux-k7".  That includes everything you need.

---

### Post by BoyOfDestiny on 2005-11-10
[QUOTE=RAOF]You want the (meta)package "linux-k7".  That includes everything you need.[/QUOTE]

I should have just told him that one first =). Oh well, that meta-package will give you the latest and greatest k7 kernel in the official repo :)

EDIT: On my 64-bit rig right now, but I think the package would be like linux-image-k7 something like that...

---

### Post by Drifter on 2005-11-10
Sorry guys for the trouble, but there are two k7 in the linux image in snaptic one is K7 the other is K7 smp.  Which one of those do I install.  Thanks for the help, I need it.

---

### Post by Sutekh on 2005-11-10
The k7-smp is for a system with multiple processors.  You just want the plain k7.

---

### Post by Drifter on 2005-11-10
[QUOTE=Sutekh]The k7-smp is for a system with multiple processors.  You just want the plain k7.[/QUOTE]


O. K. thank you so much I appreciate it.

---

### Post by Sutekh on 2005-11-10
No worries, nice to find something I can actually help with (I have the k7-smp kernel)

Have fun!

---

