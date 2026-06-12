---
title: "Multiple boot confusion"
date: 2009-08-02
forum: Installation &amp; Upgrades
---

### Post by xeddog on 2009-08-02
Sorry if this has been covered in other threads or if I should have posted in the karmic forum.  I have read several threads and all they have succeeded in doing is making my head explode.  

What I have is a triple boot system using three disk drives as follows:

SDA is a Jaunty installation that I use more than any of the others, and I want it to be the default.
SDB is a Karmic install to "play" with
SDC is a Windows 7 install also to "Play" with.

The Jaunty install on sda is working fine and has grub installed into the mbr.  The Windows 7 install was done with all of the other drives disconnected and then the other drives were reconnected.  After manually updating the menu.lst it also works fine.  Karmic was installed last and it installed grub2.  I COULD have left well enough alone at that point (well. . .ok.  No I couldn't :D ) since all systems booted, but I booted Jaunty and installed legacy grub onto sda /mbr.  I did this because I expect the Jaunty install is going to be around for quite some time while the others may come and go.

Since I did that I have been unable to boot Karmic.  I can boot Jaunty and Windows 7 ok, but not Karmic.  I get a grub "Error 15:  File not found" message.  I have looked at the /boot/grub/grub.cfg file on the Karmic disk and copied all of the information like the uuid, kernel name, etc.  to Jaunty's /boot/grub/menu.lst file, but I still get the error. 

So this comes down to one of two questions.

1.  Can legacy grub boot Karmic at all, and if so how do I do it.  If not, why not?  Perhaps something to do with Karmic formatting it's drive as ext4 ???

or

2.  Should I update the legacy grub that is installed in the mbr to grub 2?

Please remember the situation with my head and try to keep responses easy for a newbie to understand.

TIA,

xeddog

---

### Post by ajgreeny on 2009-08-02
By "legacy grub" do you mean the grub from jaunty or a previous grub version.  If it is an older version, it is just possible that the menu.lst stanza for karmic will not work because it uses the UUID in the second line.  I admit that jaunty does this also so I would expect the same problem booting jaunty, but just offer this as a possibility to you.  Just ignore this if I'm getting you nowhere.

Alternatively you can just point the grub you use to the grub menu.lst on the karmic install by editing this second line in jaunty's menu.lst.  Regrettably I have no recollection of how I did this a while ago, but a search may help you.  I think it was something like ```
configuration file  /dev/sdb/boot/grub/menu.lst
``` but I probably have got that wrong, so don't quote me on it.

---

### Post by xeddog on 2009-08-02
Thanks for the response ajgreeny.

By "legacy grub" I simply mean the grub that came with Jaunty.  I guess you could also call it grub version 1 or just grub 1.  Karmic, on the other hand, is using a new version of grub (I see it called Grub 2) and it is completely different than the grub 1 that Jaunty uses.

For starters, grub 2 does not have a menu.lst.  In the /boot/grub directory on Karmic there are many new files now.  I don't yet know they do, but the menu.lst seems to have been replaced by grub.cfg and the format is completely different than the old menu.lst.  From what I have read so far, there are other files used by grub 2 too, but I'm not there yet.  I'll try using the boot.cfg as a configuration file and see what happens.

But in the /boot/grub/grub.cfg file on the Karmic disk you can find the UUID and all of the other information that you would think grub 1 needs to boot Karmic with.  This is the information that I have used to create entries in Jaunty's menu.lst, but they don't work.  

The only other big difference that I see between Jaunty and Karmic is that Jaunty formats your disk as ext3 where Karmic uses the new(?) ext4.  Maybe grub 1 can't read ext4???  

Thanks again but "NO SOUP FOR YOU!"   :D

xeddog

---

### Post by ajgreeny on 2009-08-02
And I really wanted some soup!  Boo-hoo!

I have now found the way to point your legacy grub to the newer one on karmic, I think and thereby, hopefully boot it indirectly from jaunty.

Edit the jaunty menu.lst stanza for karmic with the following and try it out.
```
title Kubuntu Karmic Koala
configfile (hd1,0)/boot/grub/grub.cfg
```Make sure the (hd1,0) is correct, of course.  The reference I found still pointed to a menu.lst, but as you say there is no such file try the version I show, and it might still work.  If not make sure that the grub.cfg is not just a link to the real menu.lst somewhere else, which I seem to remember used to be the case in some older distros. If it is perhaps try pointing to that in the legacy grub menu.lst.

Good luck!  I hope you get this sorted and that karmic is as good as jaunty.

---

### Post by xeddog on 2009-08-02
Tried it.  Still get "Error 15:  File not found".

Sorry, but NO SOUP FOR YOU! (again)

xeddog

---

### Post by presence1960 on 2009-08-02
I would say chainload karmic from jaunty's menu.lst

I do that with Jaunty, Sabayon4.1, Mint 5 & Win 7 RC. I will post my fdisk & OS section of menu.lst. If you can't figure it out post back. Jaunty's GRUB is installed to MBR of 1st boot hard drive in BIOS that way it always comes up when I boot.

```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   5  Extended
/dev/sda2           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda3            5223       19843   117443182+  83  Linux
/dev/sda4           19844       25064    41937682+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16193   130070241   83  Linux
/dev/sdb2           16194       19457    26218080   83  Linux
raz@raz-desktop:~$ 

```

Jaunty menu.lst OS section:
```

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		9bd41049-97b3-47d5-89f3-58fe1999f4e8
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=9bd41049-97b3-47d5-89f3-58fe1999f4e8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		9bd41049-97b3-47d5-89f3-58fe1999f4e8
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=9bd41049-97b3-47d5-89f3-58fe1999f4e8 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		9bd41049-97b3-47d5-89f3-58fe1999f4e8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9bd41049-97b3-47d5-89f3-58fe1999f4e8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		9bd41049-97b3-47d5-89f3-58fe1999f4e8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=9bd41049-97b3-47d5-89f3-58fe1999f4e8 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

#title		Ubuntu 9.04, kernel 2.6.28-11-generic
#uuid		9bd41049-97b3-47d5-89f3-58fe1999f4e8
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9bd41049-97b3-47d5-89f3-58fe1999f4e8 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-11-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
#uuid		9bd41049-97b3-47d5-89f3-58fe1999f4e8
#kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=9bd41049-97b3-47d5-89f3-58fe1999f4e8 ro  single
#initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		9bd41049-97b3-47d5-89f3-58fe1999f4e8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,1)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda7.
title		Linux Mint x64 (on /dev/sda7)
root		(hd0,6)
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title		Sabayon Linux x86-64 (on /dev/sdb2)
root		(hd1,1)
chainloader     +1
```

FYI : Win 7 is on sda2, Jaunty is on sda5, Mint 5 is on sda7, Sabayon 4.1 is on sdb2. sda3 & sdb1 are ext3 data partitions and sda4 is data partition for win 7.

Sabayon & Mint have their GRUB installed to their partitions not MBR.

P.S. Sabayon uses GRUB 2. There is a grub.conf file in your /boot/grub directory that acts like menu.lst and it is editable, at least in Sabayon as root it is editable.

---

### Post by xeddog on 2009-08-04
presence1960 - 

I wish I had read your response first, but I got bored and just re-installed Karmic on sdb.  The install procedure installed grub2 into the mbr of sda and everything is working so I just left it this time.  I am going to print your response and the next time I get bored again (which may not be too long) I think I will try your suggestion.  

Thanks,

xeddog

Can't really mark this as resolved, but maybe circumvented for now.

---

