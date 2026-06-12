---
title: "Can't boot after upgrade to 8.04, or after attempted re-installs."
date: 2008-09-10
forum: General Help
---

### Post by conjtran on 2008-09-10
I had Ubuntu 7.10 and XP on my system, and was able to boot into either.  I selelected upgrade to 8.04 from the upgrade manager, and the upgrade seemed to proceed fine, but when it was finished, the system wouldn't boot into anything.  I then did an install of 8.04 from the live CD, but it still wouldn't boot after the install.  I then did an install of 7.10 from the live CD, and still it won't reboot after the install.

Seems the re-installs were a waste of time, but now, how do I get it to boot into anything?  Either XP or Ubuntu?

---

### Post by cdtech on 2008-09-10
If you want to go with the Hardy 8.04 then after the install boot from the Live CD and install the GRUB bootloader.

---

### Post by conjtran on 2008-09-11
> **cdtech said:**
> If you want to go with the Hardy 8.04 then after the install boot from the Live CD and install the GRUB bootloader.

OK, I've just installed 8.04, and now booted from the live CD, how do I install the GRUB bootloader?

---

### Post by cdtech on 2008-09-11
Once you get to the desktop, open a terminal and type "grub-install /dev/sda"

**Update::.**
I'm guessing that your XP is installed on the primary partition?

---

### Post by conjtran on 2008-09-11
OK, did that, but at first it complained that /dev/hda was not a block device, so , after reading [http://orgs.man.ac.uk/documentation/grub/grub_3.html](http://orgs.man.ac.uk/documentation/grub/grub_3.html)
Did this:
grub-install --root-directory=/media/disk /dev/hda

Same problem though.  Gets as far as:
Grub1.5

Grub loading, please wait ...

Do I need to create a separate boot partition, perhaps something has gone wrong with original boot partition?

---

### Post by cdtech on 2008-09-11
On the command line type "sudo grub" then type "find /boot/grub/stage1" and see if it see the stage files.

---

### Post by conjtran on 2008-09-11
It displays (hd0,1)

---

### Post by cdtech on 2008-09-11
> grub-install --root-directory=**/media/disk** /dev/**h**da

Your root device is the drive and partition where the files are located, ie.. --root-directory=/sda2 for the second partition on the primary drive. I think the drive to install on would be sda, can you post the output of "sudo fdisk -l"

---

### Post by cdtech on 2008-09-11
Ok, do this:
When you get to the desktop open a terminal and enter.
```
sudo grub
```
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands
```
find /boot/grub/stage1
```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)
```
root (hd?,?)
```
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```

---

### Post by conjtran on 2008-09-11
> **cdtech said:**
> Ok, do this:

OK, did that, here is a transcript:
grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


Also, following up on a previous info request
> **cdtech said:**
>  ... can you post the output of "sudo fdisk -l"


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6b3d6b3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3570    28672024+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            3571        4804     9912105   83  Linux
/dev/sda3            4805        4865      489982+   5  Extended
/dev/sda5            4805        4865      489951   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by conjtran on 2008-09-11
> **conjtran said:**
> ...
Meant to add that still can't reboot, same result.

---

### Post by cdtech on 2008-09-11
You need to check your BIOS boot order.

---

### Post by conjtran on 2008-09-18
For expedience, I just formatted everything and started from scratch, but thanks for trying to help.  Glad that I had everything backed up.

---

