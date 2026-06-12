---
title: "can't load ubuntu"
date: 2009-05-24
forum: Hardware
---

### Post by brokenwindows on 2009-05-24
I have 9.04. I ran a command for the "newer" video card after installing Wine. Now, when I try to run Ubuntu, it starts but gives me a scrambled screen. I can't actually log in or do anything. PLEASE, someone help me, I am in over my head and am back to using crappy vista.

---

### Post by SkyNet2029 on 2009-05-24
you need to do 

```
ctrl+alt+F1
```to go to the first virtual console.

Login from there. and run as root

```
dpkg-reconfiure xserver-xorg
```revert back to the old driver in selection.

reboot your machine after all changes have been made.

This should get you back to where you were.

Cheers!

---

### Post by brokenwindows on 2009-05-24
The Ubuntu screen loads with the bar underneath that fills orange. Once that leaves the screen it goes into this scrambled image. From there I get nothing.
I'm not sure when to try the CTRL+ALT+F1... I tried doing it once it appeared as though Ubuntu had loaded. It didn't work so I tried entering my user name and then password (I can't see anything that I am doing on the screen) and then tried entering CTRL+ALT+F1 and nothing still. 
I can load Ubuntu from a CD. If there is a way to go into my installed copy and modify a file, please let me know. After using Ubuntu for the short amount of time that I have, I HATE Windows. Really, I hate Windows.

---

### Post by SkyNet2029 on 2009-05-24
when you are at the grub boot screen select single user mode. once that has booted up, it should drop you to a command line
 
login as root and do:
 
```
dpkg-reconfigure xserver-xorg
```
 
select the previous driver (the one you used to use with no problems)
 
go through all of the prompts, then reboot into regular (Not single user) mode.
 
What this will do is give you a selection for choosing the graphics driver to use
for your ubuntu. It is obvious the new one does not work for some reason.

---

### Post by brokenwindows on 2009-05-24
I really appreciate all of your help but I am still stuck. 
I do not have the single user mode at the boot screen. It gives me the Grub loader and the option of loading Ubuntu 9.04 kernel 27 and kernel 27 generic also kernel 26 and 26 generic. It also has a memtest and my windows options. 
Is there a file I can modify on my installed version from running a CD? This is killing me!!! 

Thank you!

---

### Post by B07030810 on 2009-05-24
I' also new to ubuntu .I'm not sure but you can have a try.When you come to the grub loader,choose the option which isn't your general choose.Maybe it is single mode.Just have a try .It's better than do nonthing~~

---

### Post by brokenwindows on 2009-05-25
I tried going in through every option. None of them work for me. Thanks, though.

---

### Post by SkyNet2029 on 2009-05-25
Sorry for late posting. Wifi on debian died so had to rewrite some init's..Anyway..
 
When your computer is starting, there should be a brief message along the lines of "GRUB Loading... Press Esc to enter the menu". Press Esc at this prompt to select recovery mode
 
Let me know if this works for you as this is a very strange problem and am interested in the how/why/what of it.

---

### Post by brokenwindows on 2009-05-25
Please, don't worry about the late reply! I'm just happy that someone is trying to help me. I will try what you have said and post my results. 

Thank you!

---

### Post by brokenwindows on 2009-05-25
Ok, I can't hit escape to get to a menu. I tried three times and it still went to the regular loader screen. Here is what I have for options:
Ubuntu 9.04 Kernal 2.6.28-11
Ubuntu 9.04 Kernal 2.6.28-11 generic (recovery mode)
Ubuntu 9.04 Kernal 2.6.27-11
Ubuntu 9.04 Kernal 2.6.27-11 generic (recovery mode)
Memtest
Windows XP <--- this appears to be some type of recovery for Windows
Windows 7
Windows Vista

I have no screen when I choose Ubuntu, no matter which one I choose. I think that I may be stuck re-installing it. If I am, have you used the notebook remix? I use the desktop version on my laptop with no problems and I am wondering what the difference is.

Thank you!

---

### Post by SkyNet2029 on 2009-05-26
choose the recovery option mode and then do 
 
```
sudo dpkg-reconfigure xserver-xorg
```
 
unless of course you are running as root, then omit the sudo part of the command.
 
That should get you where you need to be.

---

### Post by brokenwindows on 2009-05-27
I tried that and it didn't work. I tried loading from the CD and going into the terminal on the file system. Nothing is working. I think that I am left reinstalling. I hate to reinstall after getting everything set up the way I like it.

---

