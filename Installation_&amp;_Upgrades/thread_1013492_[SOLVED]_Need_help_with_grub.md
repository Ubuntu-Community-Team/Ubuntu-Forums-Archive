---
title: "[SOLVED] Need help with grub"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by joriad on 2008-12-16
I lost my intrepid grub when I installed windows xp that was required by Magicjack. After I discovered that I no longer had internet access or my Ubuntu partition, I deleted the windows partition. Now I need to know how to get my Ubuntu partition grub back. I still have that partition in tack but cannot access it. 

Thanks
John

---

### Post by luckstrikes on 2008-12-17
Put in the UBUNTU live CD.
Start the live session.
Go to the terminal
Type
sudo fdisk -l
Find your boot partition( It is usually in tune of around 100MB having a linux filesystem like ext2/ext3. The name would be similar to /dev/sdaX or /dev/sdbX where X is a number.)
Once you get that, type
sudo grub-install /dev/sdaX  (The boot drive you found earlier)

This would get you your grub back!!! :-D

---

### Post by joriad on 2008-12-17
this is what I get from that code

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0bdd0bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8790    70605643+  83  Linux
/dev/sda3            9555        9729     1405687+   5  Extended
/dev/sda5            9555        9729     1405656   82  Linux swap / Solaris

Disk /dev/sdc: 18 MB, 18612224 bytes
1 heads, 36 sectors/track, 1009 cylinders
Units = cylinders of 36 * 512 = 18432 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?    21614887    53323488   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(21614886, 0, 13)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(53323487, 0, 7)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?     4685821    58464383   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(4685820, 0, 3)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(58464382, 0, 10)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?    51941152   105719713   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(51941151, 0, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(105719712, 0, 25)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?           1   101034070  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(101034069, 0, 12)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

what do I do from  there?

---

### Post by joriad on 2008-12-17
I forgot to mention when I enter sudo grub-install /dev/sda1 
I get this output:
Could not find device for /boot: Not found or not a block device.

---

### Post by lovelyvik293 on 2008-12-17
Please post the output of 
```

sudo grub
find /boot/grub/stage1

```

---

### Post by joriad on 2008-12-17
grub> find /boot/grub/stage1
 (hd0,0)

---

### Post by joriad on 2008-12-17
Ok, looks like I got things sort of fixed it looks as if after i unplugged magicjack everything came up different, but now it won't allow me to try and boot via the hard drive, It attempts to boot the via cd drive. I tried f8 and changed the boot device but it still tries to boot the cd. I also set up the boot order to hd0 and disabled 2nd and 3rd boot order devices so that only the hard drive would boot. but that also did not work

here is what I get now for grub setup

grub> find /boot/grub/stage1
 (hd0,0)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

grub> 

as far as i can tell this looks right.

Thanks for any help you can be.

---

### Post by joriad on 2008-12-17
All fixed now. setup grub again and restarted again and it came up with no problem.

Thanks for everyone's help

---

