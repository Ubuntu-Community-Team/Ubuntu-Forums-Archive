---
title: "need to delete GNU GRUB from a HDD"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by windowsatemyhomework on 2005-09-12
I have two hard drives, an SATA drive in position SATA-4, and an ATA-133 that is the master on the primary IDE. SATA-4 is a single partition - it is NFTS and has Windows XP on it. The IDE drive has three partitions, the largest of which has the vast majority of the space and is ext3 with my ubuntu installation. I don't know why the other two partitions are there, they were created by the debian installer. The SATA drive is recognized in Ubuntu as sda1, the IDE partitions as hda1, hda2, and hda5 (hda1 is the big partition).

I can't get into Windows at all any more, but I really need to. If I go into the BIOS and change the boot order so that it tries first to boot from the SATA-4 (the Windows drive), I get "GNU GRUB version 0.95", which lets me choose either Ubuntu or Windows. If I choose Windows, I get this message:```
  Booting 'Microsoft Windows XP Professional'

root  (hd1,0)
 Filesystem type is ext2fs, partition type 0x83
savedefault
chainloader +1

Error 13: Invalid or unsupported executable format

Press any key to continue...
```and pressing any key brings me back to the GRUB OS selection menu. So I choose Ubuntu, but I get this message:```
  Booting 'Ubuntu, kernel 2.6.10.5-amd64-generic Default'

root  (hd0,0)
 Filesystem type unkown, partition type 0x7
kernel /boot/vmlinuz root=/dev/hda1 ro console=tty0 quiet splash

Error 17: Cannot mount selected partition

Press any key to continue...
```and, again, pressing any key brings me back to the OS menu.

If I hard reboot and go into the BIOS to switch the boot order so that the IDE Master (the one with Ubuntu) is tried first, I again get "GNU GRUB version 0.95" with the same two options. If I try windows here, I get the following message:```
  Booting 'Microsoft Windows XP Professional'

root  (hd1,0)
 Filesystem type unknown, partition type 0x7
savedefault
chainloader +1
```and here the system hangs. From that same menu (when the IDE drive is first in the boot order), if I choose Ubuntu, it works. 

The issue is that I can never get into Windows. Is there a way to configure either of these GNU GRUB menus so that Windows will work from it? If not, is there a way to get rid of that menu from the SATA drive entirely, so that Windows will just automatically load if that drive is first in the boot order? Please, somebody with some understanding of GRUB help me out.

---

### Post by Bruce3000 on 2005-09-12
Ouch...

My first suggestion would really be applicable to what to do before installing a multi-boot system. Anyway... here goes... this may be an ongoing thread...

What I would have done in the first place was to install GRUB to the root of your linux partition, rather than the Master Boot Record (MBR). I've always avoided trying to boot my MS Installations (DOS, Windows - Whatever) from either LILO or GRUB, deffering to Power Quest's Boot Magic / Partition Magic 8 (which you have to pay for - or find free on the cover of a magazine). In the case of DOS, I use XOSL.

Recovery depends on where you have installed GRUB, so you would really need to tell me that.... Also, could you post the output from "sfdisk -l" so that we can see your partitions.

NTFS support in Linux is a tough one, so I think we'll see what we can do for you based on any potential damage.

Cheers

Bruce

PS. DOS 1.0 - Windows XP likes to be at the start of a hard drive! It's not as flexible as Linux.

---

