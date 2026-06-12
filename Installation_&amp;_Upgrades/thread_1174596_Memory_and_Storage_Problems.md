---
title: "Memory and Storage Problems"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by simslee on 2009-05-31
Hello everyone from a newbie,
I have just installed Ubuntu to a USB external hard drive and setup my laptop to boot in to windows if it is not connected and Ubuntu if it is and it works like a dream apart for one problem can any one help?
I installed Ubuntu for my own personal use and fun things like music ect but I think I have done some thing wrong I tried to download a program and it could not be downloaded and saved because I got the message that there was not enough space to save it, but there is as I installed Ubuntu to a 80GIG partition, also my music and vidio folders are not big enough for my files obviously I have done something wrong , HELP! 
 
Also while I have your attention is there any way of making some sort of repair disk that I could use on other pc's to make them boot into my Ubuntu external hard drive, giving a dual boot optiont he plan is to this on my desktop pc 
 
Are there any programs I should look at for playing and compiling a music libary
 
I think Ubuntu is brilliant and I love its ethos.
 
Thank you Simon
 
PS Should I have Ubuntu mobile on my laptop or am I OK with sticking wih Ubuntu

---

### Post by colonelpotter on 2009-05-31
I'm a noob but I'll try my best.  Boot into your ubuntu and then go to system,adminstrator,system monitor and then the file system tab you well see /dev/sda1 give me your total, free and available. Theres a nice program in applications, accessories called disk usage analyzer with that program you can see which folders are taking all the space. On your dual boot question If you have the space you can install ubuntu along side windows giving you a dual boot. It well install a grub boot loader so you can select which os to boot into. songbird and amarok are nice programs for your music collection.  Amarok is a kde app so it will also install some components

---

### Post by simslee on 2009-05-31
Thank you very much for your help I will try it, and I will look at songbird and amarok.
The dual bool boot is more complicated as I have already got Ubuntu on the external hard drive and I do not want to install another copy on the desktop PC but I want the option so it will boot in to the external HDD if connected so I somehow have to alter the boot ini file in windows so it will do this.

---

### Post by colonelpotter on 2009-05-31
So your saying the desktop wont boot the external ubuntu drive. If so you have to change your bios settings to something like boot usb HDD or some bios it says extra. If your desktop doesnt have the option in the bios theres no way boot the external drive. If you have a fast cpu in the desktop and 1gb or more of ram you can run a VM inside windows.

---

