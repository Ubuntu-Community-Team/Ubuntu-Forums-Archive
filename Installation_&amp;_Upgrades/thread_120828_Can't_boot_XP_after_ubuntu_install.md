---
title: "Can't boot XP after ubuntu install"
date: 2006-01-23
forum: Installation &amp; Upgrades
---

### Post by gravediggers on 2006-01-23
Did the installer detect XP present?

What menu options does GRUB give you on boot?

---

### Post by Renton on 2006-01-23
here is <b>menu.lst</b>
title           Ubuntu, kernel 2.6.12-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-10-386
boot

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

title           Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


All these options are available. When I try WinXP the error is something along the lines of:

can not boot windows xp. please check the path of the windows partition. check the windows hardware documentation etc...

---

### Post by gravediggers on 2006-01-23
??

looks good
u haven't blown away part of XP?
still have boot.ini?

---

### Post by Renton on 2006-01-23
russel@BOB:/mnt$ sudo cat windows/boot.ini
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

contents of Windows boot partition:
russel@BOB:/mnt$ sudo ls windows
AUTOEXEC.BAT                  itouch_crash_info.txt  RECYCLER
boot.ini                      MSDOS.SYS              System Volume Information
CONFIG.SYS                    NTDETECT.COM           Temp
Documents and Settings        ntldr                  winzip.log
IO.SYS                        _ok2delete

---

### Post by gravediggers on 2006-01-23
Sorry not to keep up with your replies - was getting food!

Only thing a can suggest is that you boot to your XP CD and go into recovery console, do fixmbr, and at least your XP works.

Then you can boot to a live disk (hope you've  got one) and reinstall grub manually to MBR. You need instructions??

---

### Post by Renton on 2006-01-23
I reinstalled ubuntu recently and ever since I can't start winXP. It seems as though the XP boot partition is not readable. 

**results of fdisk:**
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          19      152586    7  HPFS/NTFS
/dev/hda2              20        2432    19382422+  83  Linux
/dev/hda4            2433        4865    19543072+   5  Extended
/dev/hda5            2540        4865    18683563+   7  HPFS/NTFS
/dev/hda6            2433        2539      859414+  82  Linux swap / Solaris

Grub is installed on the MBR, all of the grub files reside on hda2

If anyone has any ideas I would much appreciate them.

Thanks in advance.

---

### Post by Renton on 2006-01-24
I will give that a try. Doing a manual grub install do I need to boot to a console and go do the whole grub install stuff?

Thanks for your help.

---

### Post by gravediggers on 2006-01-24
Can't promise to monitor this thread constantly, but pls let me Know how u go!

---

### Post by ajgreeny on 2006-01-24
If you have a floppy disk drive it's worth installing grub to floppy just so you can get back to linux without messing about with the live CD.

Check the floppy is listed in your /boot/grub/device.map, ans if not add
(fd0)	/dev/fd0
at the bottom.

Then sudo grub-install /dev/fd0

Then once youv'e sorted out your windows problem you can reinstall grub to hard disk the same way,  sudo grub-install /dev/hda

---

### Post by gravediggers on 2006-01-24
Renton,

Not sure how ur going on ur problem but try this link using ur install disk
[http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto](http://ubuntuforums.org/showthread.php?t=76652&highlight=grub+restore+howto)

or if u have live cd then 

```
$ grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
$ 
```

---

### Post by Renton on 2006-01-25
I have figured out the problem!

When I reinstalled Ubuntu the partition numbers got changed. I was always able to boot into Ubuntu so the grub on floppy would not have helped in this situation ( But I DO have one anyway). 
[B]
Old BOOT.INI:[/B]
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft...

**New BOOT.INI:**
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

Only problem was that the boot partition is NTFS and I needed windows to write to it:
/dev/hda1 * 1 19 152586 7 HPFS/NTFS

I didn't want to recompile the Kernel with NTFS write support and couldn't find a livecd with NTFS already on it. Most DOS boot disks don't have NTFS support either. Finally I found NTFS4DOS at [http://www.datapol.de/dpe/freeware/](http://www.datapol.de/dpe/freeware/)
Just installed it onto my work machine, make a bootable floppy, put the new BOOT.INI file on the floppy, rebooted with the floppy, and copied the new BOOT.INI file to the boot partition. 

Thanks again for all your suggestions. I really appreciated the help.

---

