---
title: "boot up and shut down blank screen"
date: 2006-06-04
forum: Hardware &amp; Laptops
---

### Post by NiksaVel on 2006-06-04
Hey all,

this is my first post on the forums, first of many most likely :) 


I have decided to start working with linux some two weeks ago and ran upon fedora which was my first distro...  in the meantime I realised that there is much more software easily available for debian distros so I moved to ubuntu which was succesfully installed on my laptop as dual boot with XP (I still need to play my games :)....

I had a prob with display during boot up when playing with live CD, and the same thing happened when installing - the installer was nice enough to say that I should try with vga=771 (if I'm not mistaken) and that worked great.

Now, when I installed the whole thing, I once again have a blank screen starting from grub interface till the login screen (I assume that's where x kicks in). I can work with gui fine, and once again when I shut down I have a blank screen till the laptop turns itself off.

Obviously I need to tell the boot process to use this vga=771 command, but don't know where to put that...  can some1 please help?


thanx!

---

### Post by NiksaVel on 2006-06-04
ermm...  figured it out :)   hehe

works just fine now

---

### Post by Duffman on 2006-06-06
IM having a similar problem what did you do?

---

### Post by NiksaVel on 2006-06-06
ooooohh  my first helping post..   not asking for stuff for the first time :)))


hehe

anyways, go to dir:
/boot/grub/
and open menu.lst

near the end of the file there is the menu, what you need to do is replace:

kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda3 ro quiet splash


with:
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda3 ro quiet splash vga=771


wheee... hope I helped :)

---

### Post by Ruben van Royen on 2006-10-16
Actually, you should not change the lines at the end of the menu.lst file, These lines are automatically generated when you install a new kernel.

Instead, you should add the option to defoptions. E.g.:
# defoptions=quiet splash vga=771

After that, run 
sudo update-grub

This will update the lines at the end of the menu.lst file

---

