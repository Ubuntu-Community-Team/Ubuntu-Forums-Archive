---
title: "Help with harddrive"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by tocky on 2006-07-14
Hi!

I have a problem when I want to install Ubuntu Dapper Drake, on my sata harddrive. The installation goes smooth all the way until boot up time. When the system boots up, Ubuntu can't boot from my sata harddrive. Is there anyway I can fix this. I know that the sata support on Linux is limited, but though it is no problem installing it, then it must mean that Ubunut can find the harddrive, but why can't it boot from it then.

Harddrive: Hitachi Deskstar HDS72258 0VLSA80
Motherboard: Epox 8K9A7I (VT8237 chipset)

---

### Post by tocky on 2006-07-14
Well guess I'll have to test and find out myself though it seems like I won't get any replies here. Thx anyway :)

---

### Post by scxtt on 2006-07-14
do you have other hard disks in your computer? (especially some IDE drives where grub was potentially installed) ... are you sure your BIOS is set to boot from your SATA drive?

i have 2 SATA drives in my computer, 1 w/ breezy and 1 w/ dapper - i can boot from either one ...

and 4 hours is hardly long enough of a wait period for your 2nd post ...

---

### Post by tocky on 2006-07-15
I do have a second harddrive IDE, which I now have installed ubuntu on. I was planning on doing two things, first update my bios, which failed though I can't find my floppy in Ubuntu, the second one was to try to update the kernel and then some way move the installation on the IDE drive to the S-ata so there will be better sata support on my primary harddrive. Though even this seems like a longshot, and I guess that there is other things I should try first, but the questions is what?

Ohh, and yes I'm positive that it boots from the sata

---

### Post by Soarer on 2006-07-15
I think people also need more information. You say it won't boot from your SATA  - how far does it get & what error (if any) do you see?

Mine won't boot using GRUB from my IDE - I had to use LILO instead. Maybe you have a similar problem, but who can tell? :)

---

### Post by tocky on 2006-07-15
Well I first I got the grub error but now when I try to boot it, it says the operating system can't boot. And doesn't say anything about grub. Anyway how do I install Lilo instead of Grub.

The installation goes fine, but at boot up I'm stuck, with either Grub error (no number) or as It does now it only says that the operating system can't boot.

---

### Post by tocky on 2006-07-15
Now I will try to install Ubuntu on my sata harddrive, with no other harddrives connected in the PC. Then It mght work. though I don't believe it, I simply don't have other ideas.

Well as a sidnote, it didn't work, now I get the Grub error. Don't have any clue on what to do.

---

### Post by tocky on 2007-03-04
Well after I long while, I've decided that I will get my harddrive to work with ubuntu. So I've done som massive google searching and read tons of forums etc. But still I can't get it to work, at least I got a bit further, here is my out put info.

```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10241406   83  Linux
/dev/sda2            1276        1300      200812+  83  Linux
/dev/sda3            1301       10011    69971107+   5  Extended
/dev/sda5            1301        9946    69448963+  83  Linux
/dev/sda6            9947       10011      522081   82  Linux swap / Solaris

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda2       /boot           ext3    defaults        0       2
/dev/sda5       /home           ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

```
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+15 p (hd0,1)/grub/stage2 /grub/menu
.lst"... succeeded
Done.

```

After I've done the installtion with grub, it still can't boot. I get stuck at grub loading stage 1.5, and the get the output grub harddisk error.

```
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/sda1 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/memtest86+.bin 
boot
```

I hope some of this information can be of use of someone to help me.

---

