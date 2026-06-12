---
title: "HDD detected by the BIOS but when it is plugged any OS/liveOS fails to boot"
date: 2013-09-14
forum: Hardware
---

### Post by grentthevampire on 2013-09-14
So yeah let me start it in this way

My PC (triple-boot setup with Win8, Ubuntu 13.04, elementary OS Luna) is doing really fine.... until i decided to add another partition to carry a mac os x hackintosh install.... now ofc i wanted to make a new partition and so i proceeded to added a new partition (which ive done oh so many times before) now the problem is... well let's say my inner clumsiness went berserk and tripped the electricity supply from my computer while partitioning(gparted).... SOOOO what happened next is a couple of grub rescue prompts after bios.... i've figured... well i ****ed up my HDD... now the only thing that's bugging me is whenever that messed up HDD is connected to my PC any LiveOS via USB wont boot so i cant exactly reformat it ....

Now i have a working set up after buying another HDD... everything boots perfectly EXCEPT WHEN THIS messed up HDD is plugged in.... 
so yeah well i kinda need help regarding that... i still kinda want to fix that HDD (im not interested anymore with the files inside it im just really hoping i can make it work again so i can use this as another storage medium) 
im assuming this is just prolly a software/partition table problem since my BIOS can still detect it any ideas guys?

---

### Post by grentthevampire on 2013-09-15
can i just bum this i've tried the whole day scouring the net but none seems to work can anyone help or just give an idea

---

### Post by oldfred on 2013-09-15
We do not support Hackintosh as that is against the Forum Code of Conduct. 

Did you convert a BIOS/MBR drive to UEFI/gpt?

---

### Post by buzzingrobot on 2013-09-15
Got an external unit you can pop that drive into? Connect it after the machine boots and see if a patitioner can find it.

---

### Post by grentthevampire on 2013-09-15
Sorry about that tbh im still not finished reading the forum code of conduct but i will try finishing it now...

anyway nope i didnt convert BIOS-> UEFI since i never actually finished the partitioning i was really just prepping it up...

---

### Post by grentthevampire on 2013-09-15
ive tried it only once (in windows) im not exactly sure if plugging in a hard drive while the whole system is running would read that HDD and if it safe... (is it safe?) 

however when i tried that in windows it didnt do anything at all ... i will try doing this in ubuntu now.

<--EDIT-->
ok so i did it.....well i tried connecting it while the system is running both in ubuntu and windows however both OS does not prompt anything that the HDD is connected any software (disk utility,gparted,easeus partition manager) is also not registering any change.... if i restarted it while the HDD is still connected,the OSes will simply not go past the boot/loading point...

although the ubuntu said something about a kernel panic however i cannot reproduce this message

---

### Post by oldfred on 2013-09-15
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by grentthevampire on 2013-09-16
I've actually tried that before already however the main problem is whenever this harddisk is plugged in any OS, LiveOS, installed OS as in anything will not boot :( Boot repair simply wont boot.... ever...

---

### Post by buzzingrobot on 2013-09-16
The kernel panic is your best clue so far.

It's possible that the drive was damaged during the power glitch.

---

### Post by grentthevampire on 2013-09-19
been trying to fix this all this time... still aint fixed... well i guess i can say it's officially dead (by my standards) i'll try bringing it up to some professionals hopefully they can shed some light into it... if ever this get fixed expect another post here :) till then ,thank you for your help guys

---

