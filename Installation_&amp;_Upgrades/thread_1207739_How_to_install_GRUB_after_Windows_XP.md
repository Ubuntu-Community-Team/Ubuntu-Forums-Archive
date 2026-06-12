---
title: "How to install GRUB after Windows XP"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by Richardcavell on 2009-07-08
Hi,

Ubuntu was installed to the second and third partitions of an internal IDE hard disk. The intention is that the second partition will be /boot and the third partition will be /.

Then Windows XP was installed to the first partition. It appears that the BIOS is loading from the first partition by default, which is the Windows XP bootloader. There is no BIOS option to load from the second partition. It appears that GRUB is installed on the second partition correctly, but the machine is not loading from that.

What is the correct solution? Should GRUB be installed to the first partition or to the MBR? How does the fact that the second partition is /boot change things? Does it take the grub-install command with the --root-directory switch?

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39a339a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2040    16382488+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2041        2185     1164712+  83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3            2186        4373    17575110   83  Linux
Partition 3 does not end on cylinder boundary.
/dev/sda4            4374       19457   121162230    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5            4374        4710     2706921   82  Linux swap / Solaris
/dev/sda6            4711        5269     4490136   83  Linux
/dev/sda7            5270       19457   113965078+   7  HPFS/NTFS

---

### Post by merlinus on 2009-07-08
If what you say is true, then what is this:

/dev/sda6            4711        5269     4490136   83  Linux

Look like another linux partition to me....

Also, why a /boot partition when all you are doing is dual-booting?

And I also wonder about the fdisk error messages that partitions do not end on cylinder boundaries.

---

### Post by presence1960 on 2009-07-08
Restore GRUB by doing this : 
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

In #5 use what is output from the command in #4 [should be (hd0.1) based on your sudo fdisk -l]
in #6 use setup (hd0) to put GRUB on MBR. you should be good to go when you boot. Whenever you install Windows after Linux on the same HDD the Windows bootloader overwrites GRUB if GRUB is in the MBR.

---

