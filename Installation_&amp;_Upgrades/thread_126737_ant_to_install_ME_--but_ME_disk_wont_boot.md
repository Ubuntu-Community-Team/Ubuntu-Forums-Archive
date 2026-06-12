---
title: "ant to install ME --but ME disk wont boot"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by angeleyes on 2006-02-07
I was told I needed to delete my XP partition to reinstall my  Windows ME(which I have key and disk for)but now I cant seem to get my ME disk to boot and run from start up--changed the boot order so it would boot CDROM first but it didnt help..
Please help me before my other half kills me for this..(he liked Windows better the Ubuntu-Im the other way around)I also need to make it dual bioot system.
Apprecaite any help
:(

---

### Post by DiscoKiller on 2006-02-07
you can try searching for a boot disk on the net. usually you can pick up a small exe file somewhere on the net that makes a windows boot disk for you. i dont personally have windows installed but this link may help you (i cant check myself) if u scoll down a bit u will find the link to 'Boot Disk - Windows ME boot disk with CD-ROM support'. this is the most likely of the hits i found in google to be the one that will help you out. (i`m not sure that sentece was even english) otherwise try googling around for windows boot floppy downloads and traul around to find one. tell ur PC to boot from floppy and that should let you install windows. hope this helps

DK

EDIT: The boot disk should come with fdisk so u can at least delete your partition :D

---

### Post by angeleyes on 2006-02-07
I found my boot disk for Me
Do I only delete the XP partition?How do I know which onw it is?
Im alittle scared of losing Ubuntu in the process -then I couldnt get any help

---

### Post by angeleyes on 2006-02-07
hmm my fdisk (from ubuntu)looks like this:

Disk /dev/hda: 80.0 GB, 80060424192 bytes
240 heads, 63 sectors/track, 10341 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         575     4346968+  83  Linux
/dev/hda2   *         576         852     2094120    6  FAT16
/dev/hda3           10341       10341        7560   82  Linux swap / Solaris

---

### Post by m.musashi on 2006-02-07
I wouldn't actually delete the partition on which Windows in installed. Instead, simply use the Windows install program to reformat the Windows partition (or fdisk). It's been a while since I did that with ME and I'm not real sure of the procedure. XP has it's own reinstall program that does the format (although I haven't used it on a dual boot) but I'm not sure with ME. I'd just pay attention to partion size and such and make sure things sound right before you proceed. It's certainly possible to end up reformatting the whole drive and loose partitions.

Are you trying to reinstall XP or ME? If you have an XP cd it's pretty straightforward but again, I've not done it with a dual boot. Back up the Ubuntu partition if you can or at least the important files.

---

### Post by angeleyes on 2006-02-07
[QUOTE=m.musashi]I wouldn't actually delete the partition on which Windows in installed. Instead, simply use the Windows install program to reformat the Windows partition (or fdisk). It's been a while since I did that with ME and I'm not real sure of the procedure. XP has it's own reinstall program that does the format (although I haven't used it on a dual boot) but I'm not sure with ME. I'd just pay attention to partion size and such and make sure things sound right before you proceed. It's certainly possible to end up reformatting the whole drive and loose partitions.

Are you trying to reinstall XP or ME? If you have an XP cd it's pretty straightforward but again, I've not done it with a dual boot. Back up the Ubuntu partition if you can or at least the important files.[/QUOTE]
 I want to install ME because I have the Boot disk as well as the install CD -I cant find my XP disk .we liked ME better anyway its a smaller program.

---

### Post by m.musashi on 2006-02-07
[QUOTE=angeleyes]I want to install ME because I have the Boot disk as well as the install CD -I cant find my XP disk .we liked ME better anyway its a smaller program.[/QUOTE]

Then I would try and see if you can just reformat the Windows partion with the ME boot disk or with fdisk. Of course my understanding was to always install Windows first and then Linux as it's more forgiving of dual boots. This page ([http://www.microsoft.com/windowsxp/using/setup/expert/russel_september10.mspx](http://www.microsoft.com/windowsxp/using/setup/expert/russel_september10.mspx)) page seems to contradit that so I'm not sure. However, if you reformat the Windows partion and use fdisk to set that partion active you might be able to install ME without any problems. However, I don't know if that will have any effect on GRUB and dual booting after install. I'm not that expert. I'm just relaying what I have done. I didn't search much but there may be more info on the MS site.

---

### Post by m.musashi on 2006-02-07
Another tool that might help is the ultimate boot CD [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/). I used it to reformat and partion a second IDE drive to fat32 as a file share when Windows wasn't even recognizing it.

---

