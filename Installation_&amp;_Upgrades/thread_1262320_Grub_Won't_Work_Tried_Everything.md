---
title: "Grub Won't Work: Tried Everything"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by Justin312 on 2009-09-09
Hello, 

I just finished re-installing Windows and (as expected) grub doesn't work anymore. 

I've tried everything I can to make it work but it just won't re-load. I've tried a few permutation of grub-install (from live CD) as well as (as a last resort) auto grub boot. None of these have worked. 

I'm going to paste the last set off things I tried below from the live CD (the first time around I tried the same thing without the binding). There's something going on I just can't get. 

Please help!

    Justin
[I]

mount /dev/hda5 /mnt
mount -o bind /dev /mnt/dev
mount -o bind /proc /mnt/proc
chroot /mnt


grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0,5)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu
.lst "... failed

Error 22: No such partition

grub> setup (hd0)  
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# grub
Probing devices to guess BIOS drives. This may take a long time.
root@ubuntu:/home/ubuntu# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7a1f7a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3669    29471211    7  HPFS/NTFS
/dev/sda2            3670        7296    29133877+   5  Extended
/dev/sda3            7153        7296     1156680   82  Linux swap / Solaris
/dev/sda5            3670        7152    27977134+  83  Linux 



[/I]

---

### Post by ronparent on 2009-09-09
You couldn't have tried everything yet if it not working. Were you doing the grub setup from a live cd? If not, boot to the live cd and enter the following series of commands into a terminal:

[B]sudo grub
grub> find /boot/grub/stage1
(hd0,5)

grub> root (hd0,5)

grub> setup (hd0)[/B] ###note this is (hd0) not (hd0,5) 

 At this point your grub will be back in business at the next boot. Goog luck.

---

### Post by moe458 on 2009-09-09
i think the issue lies with in

grub> setup (hd0,5) ###### pls correct ######

grub> setup (hd0)  ######correction ######

---

### Post by Justin312 on 2009-09-18
Hi, 

I still haven't managed to get this to work. I have duplicated exactly what was typed in another live session and I still have the same problem outlined in the output I have pasted: "Error 22: No such partition."

I'm very confused. GRUB has no problem finding the stage 1 files on (hd0, 5) but I can't "setup (hd0)" because there's no partition. What going on???

(PASTE FROM GRUB)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

---

### Post by Justin312 on 2009-09-18
I've also tried following the other method I've seen:

mkdir /mnt/root
mount /dev/xxx? /mnt/root
chroot /mnt/root /bin/bash
grub-install /dev/xxx

When I do this I substitute "sda5" for "xxx" and I get my the linux partition I want to boot with grub. 

But, when I do this all I get is:
sudo grub-install /dev/sda5
sudo: unable to resolve host ubuntu

---

### Post by presence1960 on 2009-09-18
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

