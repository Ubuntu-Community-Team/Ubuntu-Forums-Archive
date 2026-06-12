---
title: "Absolute newbie: dual boot hal.dll corrupt error"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by tickling on 2009-05-07
Hello
 
I tried to install 9.04 side by side with my windows XP. I have two hard disks on my system and I intended that drive C (single xp boot partition) would be resized and ubuntu would get whatever it needs. 
During installation I changed my mind as I was worried that data would be lost, I cancelled the installation, read some stuff over the net and then reinstalled 9.04.
Installation went fine. After that, I booted XP. It went fine, XP partition resized properly. So I went on to boot ubuntu from the boot menu and got
 
hal.dll corrut or missing
 
error message.
 
Here is my boot.ini:
 
[boot loader]
timeout=3
default=multi(0)disk(0)rdisk(0)partition(1)\WINNT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
C:\wubildr.mbr = "Ubuntu"
 
Now XP works fine, it's just that my new shiny ubuntu is somehow lost. Any idea ?
 
-- Thanks !

---

### Post by dandnsmith on 2009-05-07
Are you sure XP is working?
*"hal.dll corrut or missing"*
is usually reported as XP fails to boot properly - the hal.dll is 'hardware abstraction layer' and usually means you have to recover it from the installation CD.

Are you changing the HDD you boot from?

---

### Post by tickling on 2009-05-07
My XP is working fine . I know hal has to do with windows. However I am getting this message if I choose "ubuntu" from the boot menu. XP is fine.
I also checked that XP recognizes the new smaller partition properly and ran checkdisk on that and it went fine.
 
hall.dll is under C:\winnt\system32 as always and is probably working properly for XP... I am confused:confused:
 
should I just try reinstalling ubuntu ? I am just afraid that something in my system confuses the installer and it just might challenge my backup practices ...
 
Thanks

---

### Post by tickling on 2009-05-07
Well I tried this:
 
 Tried reinstalling 9.04 on top of itself. It would not allow me to reuse the partitions it created first time around.
I deleted those partitions using the installer built in partition editor and hit "back". Still it would not use that space.
I tried reinstalling to my second hard drive. The partition resizing failed in the middle. Luckily no data was lot and the partition was restored.
 
All this happened although I did checkdisk /f and defrag for both disks prior to installation.
 
Any idea what is happening here ? I will have to stay with windows ...:(

---

### Post by cholericfun on 2009-05-07
looks like you did a wubi installation, which (i think) would explain why hal.DLL can cause probs in you ubuntu install  
not sure how that works, especially if you did an extra partition for it

sounds like you didnt want to install ubuntu as wubi (i.e. inside windows) so you might need to try installing again...

in windows you should find a folder called ubuntu and some files - thats you wubi install.

theres some really good installation walkthroughs on the web - have a look

---

### Post by tickling on 2009-05-07
Thanks. I will try to clear all traces and start again. Maybe it has to do with the option "help me boot from CD" I chose on the Line CD. That installed some files on my  drive.

---

### Post by cholericfun on 2009-05-07
and have a read here if you didnt already...

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

when installing ubuntu as a seperate system on its own partition as i presume you want to you might be better off going through manual partition when the option comes up during install.

one thing that seems to irritate people a lot (including me..) doing that the first time is setting the mount point for the Linux partition..
thats just / unless you want to split you system over a couple of partitions..

---

