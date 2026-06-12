---
title: "[SOLVED] Grub loading stage 1.5.... error 22"
date: 2008-08-04
forum: General Help
---

### Post by semitone36 on 2008-08-04
Okay, Im sure you guys have heard this one a million times by now but my Im about to go back to college and I REALLY need my computer back!

So here's what happened: I bought an ASUS laptop last year with vista preinstalled on it. I had a lot of problems with vista and thats when I heard about ubuntu.  I taught myself a little about command lines and dual booting and installed ubuntu 8.04 next to vista SP2. Everything worked just fine with Ubuntu and i had some fun exploring it.  But then i tried to boot into vista from the grub menu and my computer just about exploded.  The screen went completely white except for the word ERROR in big red letters across the entire screen.

Now whenever I turn on my comp it just stops while loading the grub menu with the error 22 message (which ive learned means that a partition that grub is requesting doesnt exist). Because my comp came with vista preinstalled i dont have a hard copy of the os and i dont know enough about ubuntu's terminal to fix this mess

Id like to use this as a learning experience but mostly i just want my computer back. Please help and thanks in advance!!

---

### Post by jonnymccullagh on 2008-08-04
If you have a spare computer handy you could try burning and playing with [SuperGrubDisk]("http://www.supergrubdisk.org/") to assist when experiencing booting problems. It is menu driven and can rebuild boot menus but I have not used it with Vista.
You could also consider using any other livecd (e.g. Ubuntu) then mounting your / ubuntu partition and editing /boot/grub/menu.lst to fix your problems.
Just some ideas - maybe this will help you get started?

---

### Post by caljohnsmith on 2008-08-04
Welcome to the Ubuntu forums, semitone36. :)

How about posting the output of:
```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by semitone36 on 2008-08-05
Thanks for the responses guys!

A friend of mine lent me a copy of his partition magic iso and i decided to forget trying to reason with it and just wipe the hd.  I now run ubuntu alone and things are getting back to where they used to be. =D

---

### Post by jonnymccullagh on 2008-08-05
PartitionMagic costs money - try the GParted LiveCD and then give a copy (legally) to all your friends.

---

