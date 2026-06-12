---
title: "sos uninstall ubuntu"
date: 2008-08-17
forum: General Help
---

### Post by pythoran on 2008-08-17
hello

thank you very much for this forum it's really helping me to resolve many problems, i got a problem with my hp laptop i have installed ubuntu on it but i forget to keep windows partition so i formated all the partition and use it just for ubuntu what i'm looking for is how could i reinstall windows again because when i boot with win xp cd it says that windows didn't detect any hard disk it's normal because windows doesn't recognize linux file system please help me to formatthe hard disk in order to install windows first and than ubuntu

thank you very much

---

### Post by Elfy on 2008-08-17
IF you haven't done to much with your buntu installation it might be quickest to delete it and start again.

If you don't want to do that then you can use the gparted on the livecd to make partition for xp. You will have to reinstall grub but that is easy enough to do.

Which do you want to do? Whichever way you want to do it - boot the livecd and then from a terminal run

```
sudo fdisk -l
```

so we can how the disk is partitioned. We can carry on once we have that information.

---

### Post by pythoran on 2008-08-17
thank you very much for this answer but it a bit hard to understand that i will really appreciate if you explain more dor me and the others as you see 23 views i guess i'm not the only one thank you brother again it's kind

---

### Post by Elfy on 2008-08-17
Boot the ubuntu livecd, once it has started open a terminal from accessories paste in the following command

```
sudo fdisk -l
```

Paste the output you get here, then we can proceed

---

### Post by pythoran on 2008-08-18
thank you so much can just tell me what this command do ?

---

### Post by werries on 2008-08-18
That command lists harddrives and the partitions on them. This is information required for us to help you so that we know your layout.

---

### Post by Elfy on 2008-08-18
Indeed - you are wanting to install xp - it is better to do it at thebeginning of the drive, we need to know if ubuntu installed with an extended partition before we can start moving partitions about to get the room for xp.

If you are given a command to use there are plenty of resources available to find out what it is used for - google for the command it will be there, also open a terminal and do, in this case, but generally man command will get you what you want.

man fdisk

will get you the manual page for it.

---

### Post by LinuxRocks713 on 2008-08-18
Try this (WARNING: possible data loss! Execute with care.):

You will need an external media (iPod,USB thumbdrive,USB pendrive,network share,etc...)
```

# backup boot sector (first 512 bytes of /dev/sda)
dd if=/dev/sda of=*/path/to/external/media/*ubuntu.bin bs=512 count=1
# Make sure you have a blank partition at least 1.5GB to hold XP
# Now put in Windows XP CD (make sure it is legal)
# Now install Windows XP in the blank partition
# Boot into XP
# Make sure you have your external media
# In XP, go to the dialog to edit the boot.ini
# add a new entry called Ubuntu and C:\ubuntu.bin
# Copy the ubuntu.bin file from your media to C:\
copy *driveletter:*\ubuntu.bin C:\ubuntu.bin
# restart to enjoy ubuntu!

```

---

### Post by pythoran on 2008-08-18
this is what the command give me what do you guess

Disque /dev/sda: 60.0 Go, 60022480896 octets
255 heads, 63 sectors/track, 7297 cylinders
Units = cylindres of 16065 * 512 = 8225280 bytes
Identifiant disque: 0x000bba32

Périphérique Amorce    Début         Fin      Blocs    Id  Système
/dev/sda1               1        2550    20482843+   7  HPFS/NTFS
/dev/sda2   *        2551        7175    37150312+  83  Linux
/dev/sda3            7176        7297      979965   82  Linux swap / Solaris

---

### Post by Elfy on 2008-08-18
What is on the windows partition - is it data? Bit strange that the xp doesn't see that first partition.

Need to know what is there before we start.

---

### Post by pythoran on 2008-08-18
nothing at all i formated it to install win on it but as you see windows doesn't detect any hard drive

---

### Post by Elfy on 2008-08-18
Ok - boot the livecd and delete the partition and just leave the empty space and try the xp disc then.

---

### Post by pythoran on 2008-08-18
ok right now thank you

---

### Post by pythoran on 2008-08-18
nothing it's really boring me but i'm not going to give up i like linux , what shall i do ?

---

### Post by Elfy on 2008-08-18
I'm not sure then tbh at the moment. Will have to look - but it's a while since I installed any windows stuff...

when you formatted the drive at the beginning to ntfs did it give any errors.

---

### Post by pythoran on 2008-08-18
no error listen friend i don't want to desturbe you sorry for my english just try to help me find a solution thank you very much

---

### Post by Elfy on 2008-08-18
You don't disturb me, if I can help I will. But it won't be tonight now.

---

### Post by jerome1232 on 2008-08-18
Are you installing XP?

Is this a sata drive?

If both of those answers are yes, then I think windows just doesn't have the driver for your sata controller built in. (I get this too).

Windows will still see partitions it doesn't recognize, it'll say unknown partition, so I don't think it's the format of the drive.

There are 3 ways to get it working if that is the case.

A) In your CMOS setup you should be able to set your sata controller to an IDE compatibility mode.

B) If the laptop has a floppy disk you can copy the windows driver off of a cdrom your laptop should have come with (probably says drivers or something on it), and press F6 at the beginning of windows setup to load the driver off of the floppy.

C) Use a utility such as nlite to integrate the sata driver into a windows install disk. You would have to install windows xp into a VM like virtual box to do that.

---

### Post by pythoran on 2008-08-18
thanks jerome indeed it's what i'm thinking but unfortunetly my laptop has no flopy disk and no cd the laptop had a partition called recovery but i didn't burn that on a cd, i have just an xp service pack 2 with it, do you think if i put service pack 3 it will recognize the hard drive ?!

---

### Post by jerome1232 on 2008-08-18
I have no idea, I'm not sure if SP3 integrate newer drivers or not, I would search around in you bios (when you first boot the laptop it will ask you to hit del or F2 or some other key to enter setup) and see if you can't find an option to put your sata controller into IDE( or pata whatever you want to call it) mode, For me it's under... well let me reboot and check I'll edit it in.

I have a Phoenix Award Flash BIOS.

edit: Ok for me it is under Integrated Peripherals >> Onchip IDE >> Onchip SATA >> you can select <Disabled> <RAID> <IDE>

In order to install windows I have to select IDE for it to recognize the HDD. Although even if you have the same BIOS as me, menus can vary anywhere from slightly to wildly.

---

### Post by Ryadt on 2008-08-18
Hi pythoran... try this link [http://kadaitcha.cx/xp/cannot_install.html](http://kadaitcha.cx/xp/cannot_install.html)

hope this helps you out.

---

### Post by Elfy on 2008-08-18
I did wonder if it was something similar to that but not sure as it is a long time since I had a new enough mobo to not recognise current hardware :)

Hope that sorts it for you.

---

### Post by pythoran on 2008-08-18
thank you very much i will try this and tell you if i get somthing

---

### Post by pythoran on 2008-08-26
please let me taste this success

i have done it belive it or not, i installed windows after pain thank's for every one who tried to help me i have to say that no reply helped me but you helped me i can't ignore it thank you again, now for all the other people facing the same problem your key is hirens boot 8,6 there are many utilities concerning hard disks and partitions even mbr i'm not really sure what i have did exactly to do it but i can tell you if some one want i will find out, now i think that i deserve more coffe cups hahaha i found the solution my self and i'm ready to help

---

