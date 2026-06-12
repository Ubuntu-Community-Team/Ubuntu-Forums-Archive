---
title: "can't start Ubuntu"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by chinmaya_n on 2009-03-28
I installed Opensuse as a third OS on my system along with Ubuntu and XP.
The Grub of SUSE is showing all the three, XP is working but Ubuntu is not working. It is showing some ERROR.

Can anybody help me out how to get my Ubuntu back..! with out the lose of SUSE and XP.

Thanku:)

---

### Post by zvacet on 2009-03-28
What kind of error it shows?That will be helpful information.

---

### Post by SuperSonic4 on 2009-03-28
What are the outputs of ```
cat /boot/grub/menu.lst
``` and ```
sudo fdisk -l
``` preferably pointing out which one is ubuntu

---

### Post by tommcd on 2009-03-28
> **chinmaya_n said:**
> I installed Opensuse as a third OS on my system along with Ubuntu and XP.
The Grub of SUSE is showing all the three, XP is working but Ubuntu is not working. It is showing some ERROR.
Can anybody help me out how to get my Ubuntu back..! with out the lose of SUSE and XP.

If you would like to go back to Ubuntu's grub managing the boot of your PC, then simply reinstall Ubuntu's grub to the MBR from the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)
It should detect your Suse install, along with Windows, and add them to Ubuntu's menu.lst.

The best way to do this would have been to leave Ubuntu's grub on the MBR.  Then when installing Suse, install Suse's grub to the the Suse root partition. Then just add this to the end of Ubuntu's menu.lst:
```

title Suse
configfile (hdX,Y)/boot/grub/menu.lst
savedefault

```
Replace (hdX,Y) with the partition number for Suse (remember grub starts from zero). Also, make sure /boot/grub/menu.lst is the correct path to Suse's grub. For most distros that is the case.

This will allow Ubuntu's grub to go right to Suse's grub when booting Suse; and both OSs automatically manage kernel updates via their own grub menu.

---

### Post by chinmaya_n on 2009-03-29
> **zvacet said:**
> What kind of error it shows?That will be helpful information.

It is showing ERROR: 15 and can't find the location

---

### Post by chinmaya_n on 2009-03-29
> **SuperSonic4 said:**
> What are the outputs of ```
cat /boot/grub/menu.lst
``` and ```
sudo fdisk -l
``` preferably pointing out which one is ubuntu

```
[COLOR="Red"]linux-bb93:/sbin #[/COLOR] fdisk -l             

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0aaf0aaf                     

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3315    26627706    7  HPFS/NTFS
/dev/sda2   *        3316       35185   255995775    f  W95 Ext'd (LBA)
/dev/sda3           35186       38224    24410767+  83  Linux          
/dev/sda4           38225       38431     1662727+  82  Linux swap / Solaris
/dev/sda5            3316        9689    51199123+   7  HPFS/NTFS           
/dev/sda6            9690       22437   102398278+   7  HPFS/NTFS           
/dev/sda7           22438       28811    51199123+   7  HPFS/NTFS           
/dev/sda8           28812       31998    25599546    7  HPFS/NTFS
/dev/sda9           31999       35183    25583481   83  Linux
[COLOR="Red"]linux-bb93:/sbin # [/COLOR]cat /boot/grub/menu.lst
# Modified by YaST2. Last modification on Thu Mar 26 06:33:27 UTC 2009
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,8)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.7-9
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-ST3320620AS_5QF6WACL-part9 resume=/dev/disk/by-id/ata-ST3320620AS_5QF6WACL-part4 splash=silent showopts vga=0x317
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.7-9
    root (hd0,8)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-ST3320620AS_5QF6WACL-part9 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x317
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 8.10, kernel 2.6.27-9-generic (/dev/sda3)###
title Ubuntu 8.10, kernel 2.6.27-9-generic (/dev/sda3)
    root (hd0,2)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: windows###
title Windows
    rootnoverify (hd0,0)
    chainloader +1
[COLOR="Red"]linux-bb93:/sbin #[/COLOR]

```

This was the output.!!

---

### Post by chinmaya_n on 2009-03-29
I got my ubuntu back........!!!

plz see this thread.....

THe reason i tried to install OPENSUSE is this see this thread and help me..... plz!!
[http://ubuntuforums.org/showthread.php?t=1105963](http://ubuntuforums.org/showthread.php?t=1105963)

---

