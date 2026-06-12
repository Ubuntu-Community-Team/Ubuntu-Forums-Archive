---
title: "Cant Save Edited Menu.lst"
date: 2008-08-16
forum: General Help
---

### Post by robotman5 on 2008-08-16
i need help Saving an Edit GRUB Menu i am trying to add WIndows 2000 to the GRUB! CAN SOMEONE HELP!!!!!!!!!!!!!!!!!!!:mad: plus iam trying to overwrite the Default Menu.lst to make my edited menu.lst to add Windows! and i need to be root to do that!!!!!

---

### Post by overdrank on 2008-08-16
> **robotman5 said:**
> i need help Saving an Edit GRUB Menu i am trying to add WIndows 2000 to the GRUB! CAN SOMEONE HELP!!!!!!!!!!!!!!!!!!!:mad: plus iam trying to overwrite the Default Menu.lst to make my edited menu.lst to add Windows! and i need to be root to do that!!!!!

Hi and you can use the command ```
kdesu kate /boot/grub/menu.lst
```


Edit Kde instead of gnome :)

---

### Post by robotman5 on 2008-08-16
What Should the Windows Entry Look Like????:confused::confused::confused:

---

### Post by tamoneya on 2008-08-16
something like this assuming your windows partition is /dev/sda1
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by p_quarles on 2008-08-16
Reinstalling GRUB using the boot disk is actually the easiest way to do that. It will default to creating entries for every available OS if installed correctly.

---

### Post by robotman5 on 2008-08-16
but mine is sdb1....

---

### Post by tamoneya on 2008-08-16
then change (hd0,0) to (hd1,0)

---

### Post by robotman5 on 2008-08-16
ok i did that now What?

---

### Post by robotman5 on 2008-08-16
ok now im having this problem it says this is not a bootable Floppy disk and something else i cant remember...

---

### Post by p_quarles on 2008-08-16
> **robotman5 said:**
> ok now im having this problem it says this is not a bootable Floppy disk and something else i cant remember...
What says that?

It would save you a lot of time and us a lot of frustration if you would just carefully describe the entire problem. Put a little time and thought into composing your question, and it will greatly enhance the quality of help you receive in return. As it is, you're not making much sense.

---

### Post by robotman5 on 2008-08-16
Ok when i try to Boot Microsoft Windows that was added it says this: This is not a bootable Floppy Disk 

it askes to me to put a Floppy Disk in when Windows 2000 is on CD...

---

### Post by p_quarles on 2008-08-16
> **robotman5 said:**
> Ok when i try to Boot Microsoft Windows that was added it says this: This is not a bootable Floppy Disk 

it askes to me to put a Floppy Disk in when Windows 2000 is on CD...
Is Windows installed? Is it working correctly?

---

### Post by robotman5 on 2008-08-16
no it is not:(


i am on my dad's XP PC


and hes tryin to make WIndows 2000 work :guitar:


yes it installed 100% on the  10GB hardrive then i had to Restore GRUb to make Kubuntu Work

---

### Post by tamoneya on 2008-08-16
> **robotman5 said:**
> no it is not:(


i am on my dad's XP PC


and hes tryin to make WIndows 2000 work :guitar:


yes it installed 100% on the  10GB hardrive then i had to Restore GRUb to make Kubuntu Work

What?  I understood none of that.  Can you launch some linux OS and type this:```
sudo fdisk -l
```Then post the output here.

---

### Post by robotman5 on 2008-08-16
Sorry You Lost Me There....

---

### Post by jualin on 2008-08-16
Go to the terminal and type > sudo fdisk -l and then post the results on the forums

---

### Post by jualin on 2008-08-16
Also, why don't you try [Super Grub Disk]("www.supergrubdisk.org")?

---

### Post by robotman5 on 2008-08-16
ill try that anyway im download SuperGrubDisk WIll that Help?:confused:

---

### Post by dodle on 2008-08-16
> **p_quarles said:**
> Reinstalling GRUB using the boot disk is actually the easiest way to do that. It will default to creating entries for every available OS if installed correctly.

How do you do that?  Boot into a liveCD, go to a terminal and mount your partitions, then chroot to your mounted partition with /boot/grub on it, then inputting 'sudo grub-update'?

I hope I'm not way off.  Dont make fun of me!

---

### Post by jualin on 2008-08-16
> **robotman5 said:**
> ill try that anyway im download SuperGrubDisk WIll that Help?:confused:

Super Grub Disk should help you out.

---

### Post by robotman5 on 2008-08-16
ok when its downloaded and burnt to a Cd do i boot it while in Kubuntu? or Restart and Put the CD in then????

---

### Post by jualin on 2008-08-16
Restart the computer and boot from the CD

---

### Post by robotman5 on 2008-08-16
Ok Thanks

btw can you list what it says on Super Grub Disk so i know  what to press?:confused:

---

### Post by robotman5 on 2008-08-16
Wow Super Grub Disk is a Slowwww Download!

---

### Post by jerome1232 on 2008-08-16
the output of fdisk would still be really helpful to those helping
```
sudo fdisk -l
```

---

### Post by robotman5 on 2008-08-16
Wont that Format?


(sorry ima a Linux Use in Training!)

---

### Post by jerome1232 on 2008-08-16
No it just lists the partions on your computer like this
```
jeremy@desktop:~$ sudo fdisk -l
[sudo] password for jeremy: 

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd300d300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30515   245111706    5  Extended
/dev/sda5               1        3039    24410704+  83  Linux
/dev/sda6            3040        3101      497983+  82  Linux swap / Solaris
/dev/sda7            3102       30515   220202923+  83  Linux

Disk /dev/sdb: 503 MB, 503709696 bytes
255 heads, 63 sectors/track, 61 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000199ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          61      489951    6  FAT16

```

---

### Post by robotman5 on 2008-08-16
ok i did but its nothing like yours it doesnt display what you have...

---

### Post by jerome1232 on 2008-08-16
I know it will be different for everybody, can you post what it output?

highlight everything in the terminal press shift+ctrl+c to copy then pase it into here

---

### Post by jualin on 2008-08-16
> **robotman5 said:**
> ok i did but its nothing like yours it doesnt display what you have...

you have to make sure you copy and paste the command since the **l** on the command is not a **1** (number one) is a lower case L

---

### Post by robotman5 on 2008-08-16
ok i got this 

> [sudo] password for nick:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
nick@nick-pc:~$ sudo fdisk -l[QUOTE]

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9b6f9b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9777    78533721   83  Linux
/dev/sda2            9778        9963     1494045    7  HPFS/NTFS

Disk /dev/sdb: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1247    10016496    b  W95 FAT32[/QUOTE]


also why does it think its a FAT32?

---

### Post by jerome1232 on 2008-08-16
edit: oops spoke too soon didn't see the lower portion, so we know that windows is on sda2, which in grub speak is hd(0,1)

---

### Post by robotman5 on 2008-08-16
ok but did you read what i said up there?   ^

---

### Post by jerome1232 on 2008-08-16
Earlier you guys tried sdb1 or hd(1,0) which wouldn't have worked (it doesn't exist!) I would edit menu.l(i?)st to hd(0,1) and test it out. (you can wait for that iso to download if you wish)

It looks like XP (ntfs) is on sda2, 2k (fat32) is sdb1

If Windows XP is on sda2 and you just install win2k to sdb1. then XP  Should have a boot menu that loads up asking you to select XP or 2k. I think that's why It doesn't work trying to boot sdb1, it's probably not flagged as bootable.

---

### Post by robotman5 on 2008-08-16
the iso download is done now to burn it!


but  can someone tell me what it has?


like what can i select.:confused: on the Super Grub Disk Menu when i burn it etc....


ALSO i am just trying to Install Windows 2000 not XP!


god i dont want to do a RELOAD!

Gonna Try Super Grub Desk...

---

