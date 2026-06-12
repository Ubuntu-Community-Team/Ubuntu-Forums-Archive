---
title: "Breezy badger wont load after install"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by UM0rion on 2005-12-07
hey everyone, im new, because ive tried everything to get Ubuntu to work, and it just wont go. here's my harddrive setup, and the problems im having

2x 74gb raptors in raid 0, with windows installed on it

1x 160gb Maxtor SATA with 21GB of non-partitioned space
       the 160GB maxtor is on a PCI-SATA controller, and cannot be used with onboard sata ports

1x 13gb Maxtor IDE unpartitioned

im trying to install Ubuntu 5.10, and it will install fine, but my problem is that i cant boot it. i used bootpart to show windows to load ubuntu from the 160gb, the partition that i put linux on. it will display windows and ubuntu as options, but when i click ubuntu, it starts the bootloader, then halts, and my system has to be restarted. i THINK this is because it is on a PCI-SATA controller, but this is my first time using linux, so i dont know anything. i tried using my 13gb ide, but i can only write small amounts to it. if i try to install ubuntu on it it freezes and gives me errors. any ideas anyone?

---

### Post by teaker1s on 2005-12-07
look at [wilki ]("http://wiki.ubuntu.com/")'fakeraid'

---

### Post by UM0rion on 2005-12-07
[QUOTE=teaker1s]look at [wilki ]("http://wiki.ubuntu.com/")'fakeraid'[/QUOTE]

i dont want linux on my raid, i want linux on my 160gb SATA.. correct me if im wrong but i dont think they are the same thing...

---

### Post by teaker1s on 2005-12-07
as far as i'm aware fakeraid get's round your issue unless someone knows more that's why it's called fakeraid try searching forums for your sata install or ubuntu on sata

---

### Post by UM0rion on 2005-12-07
ok, i tried something different, i tried setting the drive with ubuntu on it to be the master harddrive. actually, i took out all my other drives, and tried a fresh install of ubuntu on the now single 160gb harddrive. it installed, grub installed itself automatcally, and when i rebooted, i got an error 17. fixing this may solve the other issue. however, im not sure where to start to try to fix this. it says somehting about grub 1.5 or something like that, then it gives me error 17. (i can deal with switching between master drives, but i just want to see linux run without a liveCD). any ideas?

i know there are a lot of posts here about error 17, and im looking through them now, but i havent found one that quite fits.. let me know if anyone has advice

---

### Post by UM0rion on 2005-12-08
update: Ok, i tried something different. I tried putting in a /boot partition first. it kinda worked once. i actually got a grub prompt. then i did somehting or another in an attempt to fix it. i cannot for the life of me get it back to where it showed the menu, despite hours of messing with it. now however, it gives me an error 15. i think the problem is where im partitioning the disks, im not doing something right. it seems common sense to me, but i might be leaving out somehting i dont know how to do yet. the last time i installed it, i created the following:

/boot
3% of 21 gb or about 630mb
primary partition
beginning of disk
use as: Ext3 journaling file system
yes, format it
mount point: /boot
options: default
label: /boot
reserved blocks: 5%
typical usage: standard
bootable flag: on

then out of the remaining space, i set this to automatically determine the useage. this in turn reset the /boot, so i went back and reconfigured it, as shown above. i then clicked to finish partitioning and format the disks. after that it closes, then restarts the computer, and then i get the error 15. can anyone point out somehting im doing wrong? if i dont do the /boot it gives me the error 17

---

### Post by bwog on 2005-12-08
You are not necessarily doing something wrong. I dont think you need a /boot partition (root /  and /swap is sufficient, /home is good as you have sufficient space), but it is harmless as far as I know.

The solution probably lies in reinstalling grub or editing grub.

Re-installing grub: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)


For editing grub look here: [http://ubuntuforums.org/showthread.php?t=99077&highlight=map+automagic](http://ubuntuforums.org/showthread.php?t=99077&highlight=map+automagic)

Check /boot/grub/menu.lst    and   /boot/grub/device.map

Because your setup is a bit complicated, it is necessary that you understand how grub works. 

I am not familiar with the settings for windows-RAID in grub. So, when you include your raid disks later, be carefull that grub does not overwrite the mbr with the raid settings at this moment. A way to definitely prevent this is to put grub on floppy (see re-install link and choose /dev/fd0).

Dont try the re-installing grub step for hours, if it doesnt work come back here.

---

