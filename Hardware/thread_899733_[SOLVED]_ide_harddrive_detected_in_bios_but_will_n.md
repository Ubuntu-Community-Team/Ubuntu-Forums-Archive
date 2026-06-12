---
title: "[SOLVED] ide harddrive detected in bios but will not grub boot"
date: 2008-08-24
forum: Hardware
---

### Post by thepizzaman on 2008-08-24
:confused: i'm using a new acer aspire M1201 with a 5000+ amd dual core and i installed a ide harddrive and the bios detect the hard drive the install works great after i add acpi=off and everything works great until the reboot and then geub starts and give me a grub error 1.5 to be exact amd i have tried different ways in the setup i have used the guided install and the manual install with the boot at the start of the hard drive nad nothing works so can someone help me out
thanks :)

---

### Post by caljohnsmith on 2008-08-24
Please boot a Live CD and post the results of the following commands:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
```
That will give us a better place to start. :)

---

### Post by thepizzaman on 2008-08-24
hd(0,0)
is that what u need?

---

### Post by thepizzaman on 2008-08-25
sorry here is the rest of it

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1eea2240

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    30732344    15366141   27  Unknown
/dev/sda2   *    30734336   268457983   118861824    7  HPFS/NTFS
/dev/sda3       268457984   625139711   178340864    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbcd4bcd4

  Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *          63   149838254    74919096   83  Linux
/dev/hdc2       149838255   156296384     3229065    5  Extended
/dev/hdc5       149838318   156296384     3229033+  82  Linux swap / Solaris

---

### Post by caljohnsmith on 2008-08-25
So do you have BIOS set up so you are booting off of the 80 GB "hdc" drive, which has Ubuntu? Based on the (hd0,0) output that Grub gave you for that find command, it looks like you must be booting hdc on startup. If that is true, then do the following commands from the Live CD:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Reboot, and see if that at least solves your Grub "1.5 error". You might have to tweak your /boot/grub/menu.lst to actually get Ubuntu to boot from the Grub menu, but see if you can just get the Grub menu on startup at this point.

---

### Post by thepizzaman on 2008-08-25
did that said that the gurb existed and then rebooted and gave me error 25

---

### Post by sandysandy on 2008-08-25
have u tried Super Grub Disk

---

### Post by thepizzaman on 2008-08-25
no i haven't and this is really my first time installing hardy
soo if u would explain

---

### Post by thepizzaman on 2008-08-25
ok i got the super grub disk laded it and tried to boot the grub on the drive and it said boot failed so anyone have any ideas?

---

### Post by sandysandy on 2008-08-25
see this

[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

[http://www.supergrubdisk.org/wiki/Howto_Fix_Grub](http://www.supergrubdisk.org/wiki/Howto_Fix_Grub)

regards

---

### Post by thepizzaman on 2008-08-25
ok i tried using the super grub disk and i tried reinstalling grub
i tried recovering it, and i tried reinstalling ubuntu and nothing worked so does anyonw have any other ideas?
and btw it said error 15 file not found even though i just installed grub:(

---

### Post by thepizzaman on 2008-08-25
anyone have any ideas?

---

### Post by jpaulb on 2008-08-25
> **thepizzaman said:**
> did that said that the gurb existed and then rebooted and gave me error 25

25 : "Unrecognized command"

This error is returned if an unrecognized command is entered into the command-line or in a boot sequence section of a config file and that entry is selected.

---

### Post by thepizzaman on 2008-08-25
did i say 25? i meant 15 :)

---

### Post by thepizzaman on 2008-08-25
anyone? :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by thepizzaman on 2008-08-26
anyone? :)

---

### Post by thepizzaman on 2008-08-28
can anyone help me? :)

---

### Post by thepizzaman on 2008-09-04
anyone??????? :(

---

### Post by thepizzaman on 2008-09-04
ok first time 32 bit now 64 still won't work any ideas?

---

### Post by thepizzaman on 2008-09-06
ok just gave up with the ide and went and bought a sata
working flawlessly :D

---

