---
title: "Cant boot. Root.disk file missing. So can't mount drive"
date: 2008-11-12
forum: General Help
---

### Post by chrisportela on 2008-11-12
Hey i would like to let you know that im not NEW the linux, i've played with it before, but im no expert. I know quite a bit about computers though. One little feather on my hat is that i know C#.net.

So my problem... Well I installed ubunutu with WUBI, and it installed the OS with no problems and it worked fine. well After installing apps, restarting, shutting down and leaving my ubuntu this morning... I come home, boot up and get the error that my root.disk file is missing and it couldn't boot ubuntu.

Where could i get this root.disk file? is there a simple way to fix this? There is the choice to reinstall but i just reinstalled because this problem happened before so i would like to know a REAL way to fix the problem.

---

### Post by chrisportela on 2008-11-12
Bump

---

### Post by caljohnsmith on 2008-11-12
The "root.disk" is in fact your entire Ubuntu partition in the form of a file in Windows; so if the root.disk file is missing, unfortunately your entire Ubuntu installation is missing. Look for that file at C:\ubuntu\disks\root.disk, and if root.disk isn't there, you're probably going to have to reinstall. My guess is that whatever antivirus/anti-malware programs you have installed in Windows might have quarantined that file, thinking that it was somehow malicious. You could search your entire HDD for any huge file the size of your Ubuntu partition, and see if you find anything. Also I would check your antivirus software logs to see if they did something with that file. Anyway, good luck.

---

### Post by chrisportela on 2008-11-12
I just looked and its right there... All 6gb of it and the swap file is there too. This is so weird... It like goes to the shell and complains to do something and then it starts issuing commands so i cant read the instructions.

---

### Post by caljohnsmith on 2008-11-12
How about posting your menu.lst; I think it's located at C:\ubuntu\disks\boot\grub\menu.lst. Also, are you using XP or Vista?

---

### Post by chrisportela on 2008-11-12
I am using Vista Ultimate SP1. All updates

The file is the txt file attached

---

### Post by caljohnsmith on 2008-11-12
So when you get that error that your root.disk is missing, do you get that after you select "Ubuntu" from the Vista boot loader screen, or after selecting Ubuntu from the Grub menu?

---

### Post by chrisportela on 2008-11-12
Well i only noticed a vista boot loader. I have not noticed where the grub loader is. I can tell you for sure that its after the vista boot loader. It begins the loading screen for ubuntu then goes to the shell and gives this message.

---

### Post by dmizer on 2008-11-12
Moved to the WUBI section. You should get more help here. :)

---

### Post by chrisportela on 2008-11-12
Thanks... I hope i can resolve the issue, cause i really like how ubuntu has taken great shape and the apps are at the quality i always wanted them to be. Which is what kept me from switching before... the apps

---

### Post by chrisportela on 2008-11-13
I'm so sorry but it seems after restarting... AGAIN it works... i would have consider this a weird bug. Its solved though. Thanks for trying to help me...

---

### Post by alcapone-g on 2008-11-20
During start up you should get list of OS on your screen.  The first should be Ubuntu 8.10, kernel 2.6.27-7-generic. your menu is set to 10s with linux as default starting up OS. Click ESC before the 10s pass. It will display you new window with small options to edit your menu. Than click e for edit
than try to change ()/ubuntu/disks on (hd0,1) it is number 1 not L letter. From your menu.lst looks like your vista is on 0 partition, most likely linux is on 1. Then click b for boot. If you have more than two partitions you may select others numbers. If it works use sudo gedit /boot/grub/menu.lst and correct your menu . I think you will have to rebuilt your linux . If you do it save your menu.lst on floppy and each time you get problem with it copy the original to /boot/grub dir overwriting the corrupted one.

---

### Post by chrisportela on 2008-11-20
well it seems i misread because its complaining about ntfs being locked by windows... so i can't boot until a proper shutdown of windows is completed... which sucks... i guess i'll just have to turn off properly from now on.

---

### Post by mpswoodwal on 2008-11-26
Hello everyone,

I have a similar problem with my Ubuntu installation.
My problem is that the file root.disk is not present in the c:\ubuntu\disks\
I tried using chkdsk /r but it was of no help, nothing was recovered either in c:\ or c:\ubuntu

Any pointers would be helpful.

My host OS is Windows XP SP3, and  using Ubunutu 8.10
This problem started when my laptop ran out of battery while running Ubuntu.

-M

---

### Post by CholericKoala on 2008-11-26
I had that problem before.  I just booted into windows, shutdown properly, then booted into ubuntu and let it do its thing.  Hope it works!!

---

### Post by mpswoodwal on 2008-11-27
I have tried rebooting gracefully 4-5 times without any luck. When I try to go check under C:\ubuntu\disks I do see swap.disk, but there is no root.disk.

---

### Post by Hello71 on 2008-12-17
First, I think the root.disk file might be hidden, try showing hidden and system files. If it's really gone, then you will probably have lost all your data.

---

### Post by ago on 2008-12-19
If you cannot see root.disk in c:\ubuntu\disks, check for a hidden folder called C:\found.000

---

