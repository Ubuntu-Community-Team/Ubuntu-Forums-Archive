---
title: "ubuntu wont boot help!!!!"
date: 2008-08-17
forum: General Help
---

### Post by djfreaky on 2008-08-17
hi im trying to install ubuntu 8.04 but i've tried the live cd and the wubi installer and non work what happens is it starts loading and then it says please remove disc and close tray (if any) and when i use wubi it just shuts off after its on the loading screen please help me!i tried reinstalling it and now i have it installed but its useless its not working at all it goes to the loadig bar then *ploop* shuts off

---

### Post by Ryadt on 2008-08-17
Check the disk for any errors.

---

### Post by djfreaky on 2008-08-17
how? i clicked check disk for errors but nothing occured and i downloaded the live cd 2 times already and used wubi. the ubuntu version is 8.04.1

---

### Post by colobix on 2008-08-17
Something went wrong under the installation, did u check the live CD for any errors before u installed it?

---

### Post by brian mcgee on 2008-08-17
I've only seen it say to remove disc after a successful install or when shutting down from the Live CD. When you first boot your computer, do you see anything that says "Loading GRUB" or similar? Does it give you a choice of operating system? (if the installer detected Windows or another OS, it should automatically create that entry for selection before boot)

Just walk through what you see as the computer boots. Also, it would be nice to have the system specs, or whatever you know about your hardware.

---

### Post by brian mcgee on 2008-08-17
> **djfreaky said:**
> how? i clicked check disk for errors but nothing occured and i downloaded the live cd 2 times already and used wubi. the ubuntu version is 8.04.1

Make sure you're booting to the CD. You might have to change that setting in the BIOS.

---

### Post by djfreaky on 2008-08-17
yeah i clicked the demo button then it took me to this ubuntu menu were i clicked the first button it started to load then shut off then i restarted it and clicked check disk for errors and nothing appeared.


can u give me a step by step guide on how to install ubuntu please cuz idk wtf im doing honestly and i really want ubuntu i've been wanting it ever since i first heard of  it back in 05

---

### Post by djfreaky on 2008-08-17
> **brian mcgee said:**
> I've only seen it say to remove disc after a successful install or when shutting down from the Live CD. When you first boot your computer, do you see anything that says "Loading GRUB" or similar? Does it give you a choice of operating system? (if the installer detected Windows or another OS, it should automatically create that entry for selection before boot)

Just walk through what you see as the computer boots. Also, it would be nice to have the system specs, or whatever you know about your hardware.

yes i get to choose ubuntu or windows vista but when i choose ubuntu it loads up the menu i click booth then it shuts off thats were my problem is

---

### Post by djfreaky on 2008-08-17
> **brian mcgee said:**
> Make sure you're booting to the CD. You might have to change that setting in the BIOS.

 do boot from the cd when i do that it says remove disc and close tray(if any) then i do that an it shuts off

---

### Post by djfreaky on 2008-08-17
if someone could help me my aim is djfreaky12 thanks

---

### Post by Ryadt on 2008-08-17
Have a try with the alternate cd.

---

### Post by djfreaky on 2008-08-17
how do i get the alternate cd?



i have the 8.04.1 alternaate iso but when i burn it its all weird its not an exe its just a folder

---

### Post by linux_tech on 2008-08-17
Are you installing Ubuntu to dual boot with another OS like Windows
or are you installing Ubuntu to run within windows (Wubi)?
Are you installing from live cd?

3 good Ubuntu Hardy Heron Installation Guides
[https://help.ubuntu.com/8.04/installation-guide/powerpc/index.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/index.html)
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

Ubuntu User Guide
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

### Post by djfreaky on 2008-08-17
> **linux_tech said:**
> Are you installing Ubuntu to dual boot with another OS like Windows
or are you installing Ubuntu to run within windows (Wubi)?
Are you installing from live cd?

3 good Ubuntu Hardy Heron Installation Guides
[https://help.ubuntu.com/8.04/installation-guide/powerpc/index.html](https://help.ubuntu.com/8.04/installation-guide/powerpc/index.html)
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.04-lts-hardy-heron)
[http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml)

Ubuntu User Guide
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

i tried both ways but i uninstalled wubi and tried the dual boot but it didnt work
now idk

---

### Post by Ryadt on 2008-08-17
> **djfreaky said:**
> how do i get the alternate cd?



i have the 8.04.1 alternaate iso but when i burn it its all weird its not an exe its just a folder
You can download the alternate cd on the ubuntu homapage. Just make sure to check the box where it ask you to check for the alternate cd.

---

### Post by linux_tech on 2008-08-17
What are your system specs?
Alternate cd is best use if you have an older computer, low memory,
as it is a text based install it uses less ssytem resources

Ubuntu download link: 
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
**Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.

---

### Post by djfreaky on 2008-08-17
my computer is brand new i have it for 3 days its an hp tx2500 with vista home premium 350gb of memory and 4gb ram and a amdturion 64 wait a minute wouldnt amd 64 be a 64 bit?


im a big stupid doodoo

---

### Post by linux_tech on 2008-08-17
Another good step by step install guide covers alternate install.

[http://www.futuredesktop.org/ubuntu8.04.html#installation](http://www.futuredesktop.org/ubuntu8.04.html#installation)

if you download the Alternate CD, it will start the installation straightaway without any LiveCD desktop.

---

### Post by linux_tech on 2008-08-17
If you have 4gb RAM, then you should have no problem running 
live cd install.  You probably have Windows Vista right? 
So you can dual boot windows and ubuntu.

Open one of the install guides.
Put the live cd in
Set bios to boot from cd
start the install
Partitioning
Choose "guided" partitioning 
Run install
Reboot

---

### Post by linux_tech on 2008-08-17
Yes AMD 64 is 64 bit

**GO here:
[http://releases.ubuntu.com/8.04.1/](http://releases.ubuntu.com/8.04.1/)
choose 64-bit PC (AMD64) desktop CD - try this first

(or
if you want to do alternate install, then choose
64-bit PC (AMD64) alternate install CD)

---

