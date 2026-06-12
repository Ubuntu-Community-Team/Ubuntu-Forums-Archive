---
title: "Laptop doesent restart correctly"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by janek87 on 2007-05-18
First, sry my english is pretty bad , but heres my problemo. 
I have a laptop and ubuntu 7.04 on it...its working very fine, but it does not restart correctly... I reboot my laptop, the screen turns to black and when the BIOS logo must be come, it doesent...the HDD led also turns on,the screen is also black, and i cant to nothing....just turn it off manuali :( . Sometimes it happens with  shut-down too, but rarely.  Ive tried the ubuntu 6.10 too, but after compiling the madwifi drivers, it fools again this way...but is it beacause of some drivers? It doesent show any errors... and i dont think its because of acpi or something...ive tried all the noacpi methods- nothing worked. oh- one thing more, before the ubuntu logo it shows BIOS Bug #81[....] - maybe this helps.

---

### Post by janek87 on 2007-05-19
anybody pls?:(

---

### Post by snakedr on 2007-05-21
Check out the following link:

[https://bugs.launchpad.net/ubuntu/+bug/38915]("https://bugs.launchpad.net/ubuntu/+bug/38915")

If your notebook is using an ATI driver this may help. 

Edit the /etc/X11/gdm/gdm.conf file and uncomment the line :

AlwaysRestartServer=true

If you are using KDE you do the same but in a different file. The url above also has instructions for that also. If this doesn't work. Try some of the other things mentioned.

The above change fixed by notebook logout hangups.

---

### Post by whayong on 2007-05-21
Do you have your splash screen enabled?  The reason why I ask is because I have the same problem and have usplash disabled, infact I took it out.  I noticed on boot, a line comes out and says something like "REBOOT disabled by hardware" or something like that.  I do not know why this is the case, but perhaps this will help narrow your problem down.  I also don't know how you could check if this is infact the case with you if you have usplash activated.  Maybe dmesg?  Perhaps someone with more knowledge can chime in.  Also, I'd like to mention that this happened in both Edgy and Feisty on my system.

---

### Post by Freaky_Llama on 2007-05-21
Whats odd is I only have the issue when there's a disc in the drive.

---

### Post by janek87 on 2007-05-24
i dont have a ATI card, i have a Intel 945GM . 
I disabled the splash screen, and wen i shut down,it says: Warning! libhal cannot shut down. somekind of HAL problem?

---

