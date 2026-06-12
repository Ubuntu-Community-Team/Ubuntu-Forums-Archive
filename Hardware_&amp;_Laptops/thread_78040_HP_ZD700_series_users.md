---
title: "HP ZD700 series users?"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by hedge on 2005-10-17
I have been running fedora core 4 for a while now and hibernation using suspend2 with the nvidia 1.0-7676 drivers just don't work worth a rip, lol!
So I'm on the hunt for a new distro! If there are any HP ZD7000 users using this distro could you please post your experiences with Ubunto?

Particularly regarding screen resolution issues, ndiswrapper, sound and of course hibernation/suspend or suspend2. 

tia

hedge

---

### Post by anonOmus on 2005-10-17
Yuppers!

Im running breezy on a ZD7000. Runs quite well, Sound works, have'nt dealt with the suspend issue as my machine doesnt get mobile too often so its a bit uneccesary for me. no major problems, does'nt detect the wireless card probably going to have to do the old wrappers trick. Also seems like im getting full res on the screen in 24 bit.

---

### Post by hedge on 2005-10-19
[QUOTE=anonOmus]Yuppers!

Im running breezy on a ZD7000. Runs quite well, Sound works, have'nt dealt with the suspend issue as my machine doesnt get mobile too often so its a bit uneccesary for me. no major problems, does'nt detect the wireless card probably going to have to do the old wrappers trick. Also seems like im getting full res on the screen in 24 bit.[/QUOTE]

Well I went ahead and installed Kubuntu and was quite pleased. Screen resolutions were correct and could actually switch from 1440x900 to other resolutions. The nv driver attenpts 3D acceleration from what I can tell by just using the GL screensavers, but it still needs the nvidia drivers to work properly. I was just  stoked to see that NTFS and NDISWrapper mods were already installed and just had to set them up. Hibernation and Suspend are still not working properly. Hibernation hangs during the initial hibernation and suspend appears to work but the usual resume is still nonfunctional. Guess I'll have a go at compiling in the Suspend2 from [http://www.suspend2.net/](http://www.suspend2.net/) .

Up to this point I'm quite pleased with this distro and happy I made the switch from Fedora Core 4.:D 

hedge

---

### Post by John.Michael.Kane on 2005-10-19
this may also help you [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsHewlettPackard)

---

### Post by anonOmus on 2005-10-20
oh yeah! heres a good website too [http://www.johnpatota.com/ubuntu/5.04.htm](http://www.johnpatota.com/ubuntu/5.04.htm) Theres alot of info on how to set up the nvidia drivers even has the right xorg.conf file for a zd7000 (running a go5600)

I would however not reccomend installing 5.10, go with 5.04 as you can always upgrade. it seems that much more is available to 5.04, and it runs a bit better. also try upgrading the kernal to 686 instead of the i386 youll see a jump in video perf. my only true bummer is the ndis wrappers for the broadcom card. you cant use a network stumbler to automatically find local wireless networks.

Stay tuned Im working on a Custom kernal for the ZD7000. When I'm set ill post the config file in this forum.

n

---

### Post by hedge on 2005-10-25
Have any of you guys recompiled a kernel and switched from the generic ide controller to the sata/ata drivers?? Or is there a module for the 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 controler??

thx

hedge

---

### Post by newbert on 2006-08-06
I'm in the same boat with the zd7000.  New to linux.  Can someone point me in the right direction for setting up wireless.

Thanks

---

### Post by poboxjoshwireless interne on 2007-04-05
ditto, me too. If you figure it out feel free to pass the info along this way.

---

### Post by dangermouse28 on 2007-06-12
Use the ndiswrapper from the repos and the .sys and .inf files from the CD which came with the machine.

---

