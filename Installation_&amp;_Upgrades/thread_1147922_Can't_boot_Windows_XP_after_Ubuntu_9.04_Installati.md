---
title: "Can't boot Windows XP after Ubuntu 9.04 Installation / Suspend to Disk doesn't work"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by ChevyChase on 2009-05-03
I recently installed Ubuntu 9.04 on the second partition of my HDD. Ubuntu works fine, however I can't boot into Windows XP anymore - GRUB just keeps hanging at "Starting up..."
I've checked the partitition and the data is still there so I think they're fine. Another thing that bothers my is that Suspend to Disk doesn't work (standby does), it will just wake up again immediately.
The computer is a standard netbook (Acer Aspire One A150L)

---

### Post by strages on 2009-05-05
I have exactly the same problem, all my partitions are still there, that is windows xp and data partitions, I can see them when I boot into Ubuntu, but If I try and boot into XP Pro, the system hangs at "Starting Up".....please help.

---

### Post by designingpatrick on 2009-10-21
I've had the same issue on 2 different computers. From what I can tell, my original OS is intact, although no option exists in boot to specify the OS. I've installed 9.04 several times on other computers with no issues. 

I also edited the boot/grub/menu.lst to supres hiddenmenu, and this gives me the option of linux, linux safeboot, and memtest.

After running sudo fdisk -l I recieve this info;

Disk /dev/sda: 4110 MB, 4110227968 bytes
255 heads, 63 sectors/track, 499 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d381

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         173     1389591    b  W95 FAT32
/dev/sda2             174         499     2618595    5  Extended
/dev/sda5             174         477     2441848+  83  Linux
/dev/sda6             478         499      176683+  82  Linux swap / Solaris

It seems like I should add Windows XP to the boot.lst around this point;

## ## End Default Options ##
# title        Windows XP
# root        (hd0,0)
# savedefault
# makeactive
# chainloader    +1

Does that seem like a good idea?

I don't know what to make of it...
Suggestions?

I found some information on another thread which provides instructions for booting into windows after installing ubuntu.

I found that after repairing windows with the "fixmbr" and "fixboot" I am able to start Windows, but I don't have any options for booting into Ubuntu now. So....

---

