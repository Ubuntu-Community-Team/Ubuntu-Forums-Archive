---
title: "Grub error 17 and/or 21"
date: 2009-08-03
forum: Installation &amp; Upgrades
---

### Post by sertrbl on 2009-08-03
As a preface, I kind of screwed around with something i shouldn't have... Really, I was feeling foolishly brave and wanted to install Ubuntu on my external hard drive, while using vista on my laptop. Chances are I don't really know what a jargon word means, so please try to keep that in mind... I will try to provide as much info as possible, but I don't know whats important.

so I burned my freshly downloaded Ubuntu 9.04 ISO and restarted my laptop, with the external 1T drive connected by USB. i entered the BIOS settings, set the boot order to 
1 CD
2 USB device
3 Hard drive
then the hard drive order to
1 1T external
2 320G internal

when I when i got to the menu, i selected language etc. and then was taken to the partition selection screen... here is where I believe I messed up. well, at the top it showed me the contents of my 1T, all blue (listed as /dev/sda, I think), and I clicked install side-by-side, and clicked continue when it asked if i wanted to write current changes. maybe that did something to the internal, which was unplanned. when that didnt seem to do what I wanted, i went back and then clicked manual, then created a partition in my ext drive, went back, and I think there was a 4th option that i clicked on, moved a slider to about half of the 1T, and clicked forward. this time I went through and finished all the info, restarted, and error:

it doesnt list possibilities to boot from, but when my external drive is plugged in, i get error 17, unplugged gives me error 21. after uninformed surfing, that tells me i replaced my windows bootloader with grub, but everything else is on the external?

so i took my Asus recovery disk and tried to restore all the vista stuff, but when i came back later it gave me error 21 from grub again.

the end goal is to have vista on my laptop, and for that to work normally, but if i start my laptop with the external drive in, it goes to Ubuntu instead. any help would be GREATLY appreciated, as i'm about smashing my head against a wall atm.

OH! and i read something about a supergrub disk... i have literally no way of obtaining that. kind of a catch 22, unless there is another way?

---

### Post by presence1960 on 2009-08-03
Because you have a recovery disc, not an installation disk you don't have access to Vista's recovery console. [Go here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") to download the iso and burn the image to CD/DVD. When complete boot from the CD/DVD and follow [these instructions]("http://ubuntuforums.org/showthread.php?t=1014708") for restoring Vista's bootloader. That's all you need to do to get Vista running again. Currently you have GRUB on MBR of your internal disk. This will restore Vista to MBR. Should be good to go after this.

---

### Post by sertrbl on 2009-08-04
EDIT: the link to download the ISO didn't work.

ah, but that doesnt solve my error 17 problem... that still wont let grub load ubuntu, will it? for the sake of time, here are various files that apparently are important for diagnosis of the problem:

device.map
(hd0)    /dev/sdb
(hd1)    /dev/sda
this is right, as i want my sdb (external drive) to be first. it is also that way in the BIOS.

relevant portion of menu.lst
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        138807db-f15e-4741-a5b4-3921dbb1e6bb
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=138807db-f15e-4741-a5b4-3921dbb1e6bb ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        138807db-f15e-4741-a5b4-3921dbb1e6bb
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=138807db-f15e-4741-a5b4-3921dbb1e6bb ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        138807db-f15e-4741-a5b4-3921dbb1e6bb
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1

sda is internal, sdb is external... fdisk:Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1402    11261533+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *        1403       30402   232935995    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcbce2081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60789   488287611    7  HPFS/NTFS
/dev/sdb2           60790       62034    10000462+  83  Linux
/dev/sdb3           62035       68113    48829567+  83  Linux
/dev/sdb4           68114       69358    10000462+  82  Linux swap / Solaris

sdb1 is a big chunk of stuff i want to ignore... basically backup for windows systems and whatnot.
sdb2 has a mount point of / and is Ext3
sdb3 is mounted /home and is also Ext3
sdb4 is of course swap
all my boot files are on sdb2, im not sure it says sdb1

again, if more info is required, im willing to provide it. this is a fresh install, so i dont know why its giving me problems right away.

---

### Post by oldfred on 2009-08-04
I see both a UUID and root entry for your first Ubuntu entry in menu.lst, I have never seen that and (hd0,1) is the same as your windows entry. Did it get enter by accident?
More info on Grub error 21:
[http://members.iinet.net.au/~herman546/p15.html#21]("http://members.iinet.net.au/%7Eherman546/p15.html#21")

---

### Post by merlinus on 2009-08-04
As oldfred said, this one has got to go, because windows is on (hd1,1):

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
chainloader    +1

and change this:

title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1

to:

title        Windows Vista (loader)
rootnoverify    (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader    +1

and restart.

---

### Post by sertrbl on 2009-08-04
"I see both a UUID and root entry for your first Ubuntu entry in menu.lst"
oh, forgot about that. i did that, trying to get something else to work

the goal is to have the vista booter on the internal, and grub on the external. im working on getting the vista loader back, as i accidentally installed it there first.

im a little confused as to this whole hd0/hd1 thing. in bios, the external drive sdb is to load, then the internal sda.
device.map reflects this, and says hd0 is sdb and hd1 is sda.
basically, does grub still think sda is hd0?  should i change menu.lst to fit, or should i just suck it up and let sdb stay as hd1?
I guess the question i should be asking is: what exactly does the change proposed by merlinus do that will remove error 17?

thanks oldfred, that was MUCH more imformative than just about everything else I have seen yet.

---

### Post by merlinus on 2009-08-04
The best way to find out is to try it.  At this point, it would seem you have nothing to lose.

---

### Post by presence1960 on 2009-08-04
> EDIT: the link to download the ISO didn't work. That is strange as I downloaded it right after I posted the link. Worked fine for me.

Sometimes Ubuntu and GRUB read disk order differently than the way they are set to boot in BIOS. Regardless of what sudo fdisk -l reports your sdb is hd0 and sda is hd1. merlinus is right about your vista entry. add his suggestion to menu.lst.

This is an ongoing problem with Ubuntu. When I installed Sabayon there is a window where you can change the order of drives to match your BIOS. Maybe one day Ubuntu will add this feature to it's installer.

---

### Post by presence1960 on 2009-08-05
I checked again today and the link to download is still working!

---

### Post by sertrbl on 2009-08-05
yea, the link ended up working later for me. I currently have windows back up on my internal HDD (I actually need it that way for college, thus all the flaming hoops I was trying to jump through)
when I first followed those instructions, im pretty sure it tried to edit the hard drive, because when I restarted it gave me a whole NEW error. I unplugged the drive, it went back to error 21, so I re-fixed the boot sector and now all is well with my windows drive
well, except that it has windows on it...
anyway, since it never worked in the first place, I may just reinstall Ubuntu and grub, if nothing else works, since I've screwed with it so much.

UPDATE:
Well, first thing I did was try to boot from the external, to get to Ubuntu. *Disk* read *error* - Press *Ctrl*+*Alt*+*Delete* to Restart
I believe that's what it said, but either way I booted from the CD. first thing I did was change BIOS to set the internal, sba, first. I figure that way everything can be consistent, and I changed device.map back accordingly.
A guide oldfred linked to also had a solution for error 17 sometimes... so I did what that told me. Basically, I used the partition editor to:
1, take the boot flag off sdb1
2, place the boot flag on sda2
3, check both disks for errors

after that, trying to boot from the external drive just takes me to a black screen with a blinking cursor. I figure that either I installed something windows boot on sdb1 accidentally when I fixed windows earlier, or replaced something on sdb2, or it could be that my computer just doesn't want to boot from the external drive. I'm going to reinstall grub once more, and see where to go from there.

one more update:
reinstalled Ubuntu, since that was the easiest way to get everything back to default. brings me back to good ol' error 17.

---

