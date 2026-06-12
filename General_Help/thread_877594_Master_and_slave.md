---
title: "Master and slave ?"
date: 2008-08-01
forum: General Help
---

### Post by mikedemario17 on 2008-08-01
i got a harddrive on master...what if i put one on slave...when i boot up will it ask me everytime what one i want...or what? and if i put a XP on master and linux on slave will there be problems?

---

### Post by phidia on 2008-08-01
With IDE drives that's generally taken care of in bios. You will need to change the jumper settings-usually anyway-from single to master-on the master and to slave on the slave drive. 
What asks you anything at boot is the bootmanager-provided you install ubuntu successfully it will detect your other OS and include it in a menu for you to select from. 
BTW the best way to do a dual boot like you want is to install windows first and then ubuntu. You also might find [this page]("https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems") interesting. See "Dual Booting Tricks".

---

### Post by arvevans on 2008-08-02
The "master" and 'slave" jumpers on your hard drives (and on the CD-ROM or DVD drives) refer to hardware addressing.  This is used to set the drives as hda, hdb, etc. in Linux (Microsoft is similar).  Depending on drive type and Linux version they may be called sda, sdb, etc.

When you make partitions on those drives this will map to file system mounts which are used by your OS in determining which drive has the boot tracks, which is the primary MS-Windows drive or which is the primary Linux drive.  Partitions on Linix drives may be noted as hda1, hda2, hdb1, hdb2, and so on with the number indication a particular partition on a specific hard drive.  On newer Linux systems the drives may be called "sda, hdb, etc." instead of "hda, hdb, etc.".

Something like this would be normally encountered in a Linux system:
[INDENT]
/dev/sda2 on / type reiserfs (rw)
/dev/sda1 on /boot type reiserfs (rw,notail)
/dev/sda4 on /home type reiserfs (rw)
[/INDENT]

This shows that in my system the base system is mounted on drive sda, partition 2.  sda partition 1 is the boot file system and contains boot files for Linux.  sda drive partition 4 is used for /home, which supports user specific directories and files. While the "mount" command does not show it, I also have a "swap" partition established as /dev/sda3 which in Linux is used as transcient memory space, much like the swap partition  on MS-windows OS.

If I added a second hard drive on the same controller cable and set it's hardware address as "slave" it would show up in Linux as /dev/sdb, with it's configured partitions numbered to show their positional relationship on that drive.

In your computer you can have 4 drives.  This includes hard drives, CD-ROM drives, and DVD drives.  You have two drive controllers on your motherboard.  Each of these can have one "master" and one "slave" drive on their connecting cable.  When installing a second hard drive, if it is connected to the same controller cable as another drive, one of these will have to be set as "master" and the other as "slave".  If your new second drive is connected via the second controller cable and there is no other drive on that cable, it can be set as either "master" or "slave", but setting it as "master" would be conventional practice.

Arv
_._

---

### Post by mikedemario17 on 2008-08-02
thanks

---

### Post by Ingenue on 2008-08-02
Ok, I totally though the wrong thing from the title of this thread. :redface:

---

### Post by mikedemario17 on 2008-08-02
> **Ingenue said:**
> Ok, I totally though the wrong thing from the title of this thread. :redface:
hahaha

---

### Post by Ingenue on 2008-08-02
> **mikedemario17 said:**
> hahaha

8-)

---

### Post by mikedemario17 on 2008-08-02
after i posted that i was like hmmmm

---

### Post by brianuk on 2008-08-02
Hi Folks, I hope this isn't to off topic but I have a dual boot problem and hope some kind and knowledgable person can help me.:)
My regular setup was XP installed on a sata drive with Ubuntu installed inside it using Wubi which worked very well.

I installed a second sata drive to install Ubuntu on and when I made the Ubuntu installation I disconnected the XP drive my reason being that I wanted to select the boot drive from the bios rather than have grub mess with the HDD mbr.

All worked well booting from XP and I could read/write an NTFS partition on the Ubuntu drive but when I booted up on the Ubuntu drive it failed to see the XP drive.

So folks is there a command to list all drives that are attached to my machine and then a command I could use to mount the drive so that I can access the drive from a Virtualbox XP image.

May I also say a big thank you to this forum and its members for all the information and help that is available to this noob Linux user,
many thanks to all of you. :)

---

### Post by mikedemario17 on 2008-08-02
post a new forum? come on

---

### Post by brianuk on 2008-08-04
Thanks for your time but I found the answer elsewhere,
it was.

run this command in the terminal
**sudo gedit /etc/hal/fdi/policy/preferences.fdi**

Edit/change the "false" values to "true" in this section
  <device>
    <match key="storage.hotpluggable" bool="**true**">
      <match key="storage.removable" bool="**true**">
        <merge key="storage.automount_enabled_hint" type="bool">**true**</merge>
      </match>
    </match>
  </device>

---

