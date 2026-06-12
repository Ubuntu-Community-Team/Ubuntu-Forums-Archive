---
title: "windows xp and grub. fresh install"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by noname580 on 2009-06-20
So i did a fresh install of windows xp MCE.  then i installed ubuntu 9.04.  First time i tried to manual create partitions and such.  when i reboot no grub. straight to windows. gr.  then i delete the ubuntu partition and try installing by choosing the first choice saying about choosing at boot. still no grub. double gr.  not sure if i would have been better off installing ubuntu first, creating a NTFS partition, and then installing windows.  Though my windows needs to have a recovery partition.  No install cd.  So now im not sure quite what to do.  If your response could be well detailed it would be nice.  Some of the stuff is new to me.  I have been using ubuntu for 6 months or so now, so that part isnt.  just the dual booting.  Thank you in advance for your time and responses

---

### Post by merlinus on 2009-06-20
If you can run from the live cd, open a terminal and post results of:

```

sudo fdisk -l

```

---

### Post by noname580 on 2009-06-20
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23969   192530961   83  Linux
/dev/sda2           23970       24321     2827440   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbaacbaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2490    20000893+   7  HPFS/NTFS
/dev/sdb2           13493       14596     8867880    c  W95 FAT32 (LBA)
/dev/sdb3            2491       13492    88373565   83  Linux

Partition table entries are not in disk order


now the first HDD isnt the problem thats my storage one.  its the second one, as if that wasnt noticable. i did try with a GParted LIVE cd go in and label sdb3 as boot but after restarting sdb1 still was lableed as boot. as at the end of install where it gives you a run down of what it is going to do there is the advance button.  i clicked that and grub was selected to be installed on hd0. anymore info you need let me know

---

### Post by merlinus on 2009-06-20
Linux does not need a boot flag.  Why don't you change the booting order in bios, since both oses are on hdb?

If not, then you can try this:

```

sudo grub
root (hd1,2)
setup (hd0)
quit

```

You also may need to edit the windows entry in /boot/grub/menu.lst.

---

### Post by noname580 on 2009-06-20
well i tried going into my bios and the only thing i can change are what HDD to read first.  there is no operating system on my large 200 gig so that doesnt help. then i tried the terminal way with the commands you told me and still no.  so i know i have to edit the menu.lst.  here is what mine says.  i just copied the important stuff.  thank you so far by the way


## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        e807ff05-10e6-4013-8659-aa17ace586ef
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e807ff05-10e6-4013-8659-aa17ace586ef ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        e807ff05-10e6-4013-8659-aa17ace586ef
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=e807ff05-10e6-4013-8659-aa17ace586ef ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        e807ff05-10e6-4013-8659-aa17ace586ef
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5a4e554b-285b-4da5-ae5e-d38dbf6d003a ro splash vga=791 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5a4e554b-285b-4da5-ae5e-d38dbf6d003a ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, memtest86+ (on /dev/sda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows NT/2000/XP
rootnoverify    (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows NT/2000/XP
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by merlinus on 2009-06-20
Comment out all these lines by making sure there is a hashmark (#) at the beginning of each:

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5a4e554b-285b-4da5-ae5e-d38dbf6d003a ro splash vga=791 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode) (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5a4e554b-285b-4da5-ae5e-d38dbf6d003a ro single 
initrd        /boot/initrd.img-2.6.28-11-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title        Ubuntu 9.04, memtest86+ (on /dev/sda1)
root        (hd0,0)
kernel        /boot/memtest86+.bin  
savedefault
boot

and delete these:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title        Windows NT/2000/XP
rootnoverify    (hd1,1)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by presence1960 on 2009-06-20
In BIOS make sure your disk with your OS is set to boot first. If you ran merlin's terminal commands then change your windows entry in menu.lst to this :

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Windows NT/2000/XP
rootnoverify (hd0,0)
chainloader +1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title Windows Recovery
rootnoverify (hd0,1)
chainloader +1
```

Sometimes BIOS and Ubuntu read drive order differently. If your sdb disk is first in boot order that is why your windows entry needs to be (hd0,0) and recovery (hd0,1). Don't ask me why but that's what works. Try it out!

here is mine> 
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4569    36700461    7  HPFS/NTFS
/dev/sda3            4570       29879   203302575   83  Linux
/dev/sda4           29880       30401     4192965   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14519   116623836   83  Linux
/dev/sdb2   *       16478       18389    15358140   83  Linux
/dev/sdb3           18390       19457     8578710    7  HPFS/NTFS
/dev/sdb4           14520       16477    15727635   83  Linux

My windows is on sda1, but note my menu.lst entry:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader	+1

reason: my sdb disk is first in my boot order.

P.S. map entries are needed when windows is not on the first boot device. It "tricks" windows into thinking it is first

---

### Post by noname580 on 2009-06-20
i tried what you guys said and still no grub. one more thing to try and then im trwoing in the towel.  im going to try deleting windows and installing ubuntu first then reinstall windows and use the terminal commands for grub that merlin stated first.  maybe that will help. if not then im lost. thanks for your help though i appreciate it

---

