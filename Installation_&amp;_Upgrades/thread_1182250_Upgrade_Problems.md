---
title: "Upgrade Problems"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by XmINiX on 2009-06-08
I recently upgraded to 8.10 (So i could then upgrade to the version 9 or simply reinstall windows.) I wanted to upgrade because Grub wouldn't let me read ANY disc to boot from. It would simply load ubuntu from my hard drive no matter what i chose to load. I upgraded, let it reboot and found that on the login screen i couldn't do anything (Move the mouse, type, anything..) I found some recovery OS or something and managed to get to the root console. I decided i'd delete the partition and then hopefully grub would be completely gone along with everything else so i could boot from a cd and install windows (Not because i'm unhappy, just because i would like to play games and stuff.) Now i get grub error 22 (of course), and still am unable to boot from a cd. I can't do anything at all, the bios wont allow me to change anything really.. It just sits there with the Error 22 on the screen. I'm stuck, i need help. You guys tell me what to do, please. It's a laptop by the way..

---

### Post by LMZKJ on 2009-06-08
Do you currently have windoze installed?  If you are basically starting from scratch, I would suggest that you go back and install Windoze first.  Create a partition of whatever size you want for windows and then let the install finish.  Once that is done, go back in and install Ubuntu.  One of the default options is to leave the windows partition and install ubuntu to the rest of the drive.  It will load grub and it has always allowed me to see both OSes on boot.

I hope this helps!:D

---

### Post by XmINiX on 2009-06-08
I'm sorry, i guess it wasn't clear. I can't boot ANYTHING. It won't boot from a cd at all. And i have nothing to try like an extra cd drive to hook up, external HD, anything. I need it to boot from a CD, if it did i would be happy. But it wont do anything, i set it to boot immediatly from a CD and it simply goes to Grub and gives me error 22.

---

### Post by metalf8801 on 2009-06-08
Can you describe what happens when you try to make changes in the bios and have you tried booting from a flash drive?

---

### Post by XmINiX on 2009-06-08
> **metalf8801 said:**
> Can you describe what happens when you try to make changes in the bios and have you tried booting from a flash drive?
 What changes would i make? I'm not sure if the bios is really what i consider it to be but, on my computer you press f2 and it takes you to a menu that shows Your hd, cd drive name, time and date, and then lets you select the order in which i tries booting things from. It makes the changes. Grub just wont let me boot from anything, i'm about to try a flash drive but what would i put on it? i only have a 256mb one available because i broke my 2gb one..

---

### Post by metalf8801 on 2009-06-08
> **XmINiX said:**
> What changes would i make? I'm not sure if the bios is really what i consider it to be but, on my computer you press f2 and it takes you to a menu that shows Your hd, cd drive name, time and date, and then lets you select the order in which i tries booting things from. It makes the changes. Grub just wont let me boot from anything, i'm about to try a flash drive but what would i put on it? i only have a 256mb one available because i broke my 2gb one..

you should be able to change the boot order so that your laptop can then boot from your CD-Rom drive you need to make sure that the changes you make are saved

---

### Post by XmINiX on 2009-06-08
I've done that..

---

### Post by metalf8801 on 2009-06-09
trying put Xpud on your flash drive [http://www.xpud.org/download.en.html#tab-2](http://www.xpud.org/download.en.html#tab-2)

---

### Post by XmINiX on 2009-06-09
I put it on my flash drive (Unzipped it into the flash drive) and it still will not let me boot from anything, it simply shows the black grub screen that says error 22 or whatever. Could i take the computer to a shop and allow them to replace the HD? Because i would like a bigger HD. lol. Or is changing HDs pretty simple? If it's possible i would like to keep this one but i'm not sure what to do. If theres anything i can do that would cost money what would the options be?

---

### Post by XmINiX on 2009-06-09
I noticed my HD slides right out, would replacing it work? I have the money for a new one and would like to have a bigger one. 
Thanks,
 XmINiX

---

### Post by metalf8801 on 2009-06-09
take out the hard drive and try to boot from a CD or flash drive if that works then getting a new hard drive might work

---

### Post by XmINiX on 2009-06-09
I took out the hard drive, put the cd in and it worked fine. So then i took out the hard drive, threw the XP cd in and then put the hd in rofl. It probably wasn't good to do that, but i dont know what else i could do. And so far it seems to be working.. I'm installing XP right now.
Thanks for the help guys!

---

### Post by metalf8801 on 2009-06-10
> **XmINiX said:**
> I took out the hard drive, put the cd in and it worked fine. So then i took out the hard drive, threw the XP cd in and then put the hd in rofl. It probably wasn't good to do that, but i dont know what else i could do. And so far it seems to be working.. I'm installing XP right now.
Thanks for the help guys!

Its great that its work for you now! If you try Ubuntu again maybe should use Wubi so that you don't have to deal with grub.  Wubi install Ubuntu inside windows like its a regular program and then at boot you use the windows boot loader to pick which OS you want to use. There are some down sides but for the most part it just the sames as a regular install.  Oh and Wubi now come on the Ubuntu live CD just put the CD in your computer when our already running Windows.
[http://wubi-installer.org/](http://wubi-installer.org/) 
 
PS 
I hope you consider trying Ubuntu again and I hope thing but better next time

---

