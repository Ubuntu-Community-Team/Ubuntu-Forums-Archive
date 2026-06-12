---
title: "Swap Partition as a logical partition?"
date: 2009-08-15
forum: Installation &amp; Upgrades
---

### Post by mostafa178 on 2009-08-15
Would it be possible for me to make one extended partition that contains the swap partition along with /root and /home.

---

### Post by Partyboi2 on 2009-08-15
Hi, yes you can do this.

---

### Post by mostafa178 on 2009-08-15
I would still be able to dual/triple boot even if I did this, correct?

---

### Post by Partyboi2 on 2009-08-15
I have my partitions setup that way and have no problem dual booting.

---

### Post by mostafa178 on 2009-08-15
Thanks for you lightning fast reply!

---

### Post by presence1960 on 2009-08-15
Yes, because linux does not need to be on a primary partition to boot. But if you are going to install windows you should put it on a primary partition.

---

### Post by mostafa178 on 2009-08-15
Thank you. Also, is there a list of the supported drive formats that Ubuntu 9.04 can read and write too?

---

### Post by OooBuntuRox on 2009-08-15
> **mostafa178 said:**
> Would it be possible for me to make one extended partition that contains the swap partition along with /root and /home.
 
You shouldn't have to worry about that too much. I found it easiest to boot with the live demo cd. Then select the install icon from the ubuntu desktop. During the setup process the partioner will start and allow you options for partioning the hard drive. If you are setting up a multiboot and already have another OS, the partitioner will ask if you want to install them side by side. I don't like this option because if either of the OSes fail you will not be able to access any of the disk without doing a complete reinstall of both OSes. Not easily anyway.
 
While I don't know if what you want is possible, I have never been able to set up the \root partion and swap partion together. If you notice, Linux always seems to want a seperate partion for the Swap area. I would make the root a primary and , yes, the swap as a logical partition. I usualy make the swap area about 10 - 15 % the size of the root or primary partition.
 
If you aren't doing a multiboot drive, then just select the "use entire disk" option in the partitioner. Ubuntu will take care of the rest by seting a root and a swap, the sizes, and the partition types (such as ext3, etc). 
 
The third option is custom partition. The only time I tried this was after another OS was installed first and I was testing the option of a multiboot system. In that case, the first OS partiton is primary, then the root Ubuntu partion is primary and the swap is either type "logical" or "swap" depending on when you partion the drive and with what OS you partition it. By the time Linux (Ubuntu) is installed there WILL be a partion labeled "swap". That has been my experience anyway.
 
It is easiest to always install Linux as the second (or last) OS. If you install it first, the multi boot often fails and you can only boot to one OS which turns out to be the last OS installed.  Then you have to go in and repair the boot process... or, start all over again.
Good luck, OooBuntuRox :guitar:

---

### Post by OooBuntuRox on 2009-08-15
> **mostafa178 said:**
> Thank you. Also, is there a list of the supported drive formats that Ubuntu 9.04 can read and write too?
 
Yes, they are in a drop down list during the install. It does default to certain types but i never pay attention to it because the default has been fine for me. There are quite a few though.
 
OooBuntuRox:guitar:

---

### Post by presence1960 on 2009-08-15
> While I don't know if what you want is possible, I have never been able to set up the \root partion and swap partion together. If you notice, Linux always seems to want a seperate partion for the Swap area. I would make the root a primary and , yes, the swap as a logical partition. I usualy make the swap area about 10 - 15 % the size of the root or primary partition.

Not true! here is my sudo fdisk -l output:

```
raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   5  Extended
/dev/sda2            5223       19843   117443182+  83  Linux
/dev/sda3           19844       25064    41937682+   7  HPFS/NTFS
/dev/sda4           25065       30401    42869452+   7  HPFS/NTFS
/dev/sda5               1        2350    18876312   83  Linux
/dev/sda6            2351        2872     4192933+  82  Linux swap / Solaris
/dev/sda7            2873        5222    18876343+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16193   130070241   83  Linux
/dev/sdb2           16194       19457    26218080   83  Linux
raz@raz-desktop:~$ 
```

sda1 is an extended partition which contains sda5 (Ubuntu /) sda6 which is swap and sda7 (Mint5 /) all are logical partitions.
sdb2 is Sabayon 4.1 / This is a primary partition.
sda2 and sdb1 are linux data partitions
sda3 is NTFS data partition 
sda4 is Windows 7 RC

You can create all your partitions using the [gparted Live CD]("http://gparted.sourceforge.net/livecd.php") or boot the Ubuntu Live CD and when desktop loads open a terminal and run this command ```
gksu gparted
```. I prefer the gparted Live CD because it is more current and you can create NTFS partitions. Once you have your partition scheme created you can install Ubuntu by choosing the manual option. Do not use "use entire disk" or "guided resize"

If you want to use suspend/hibernate it is recommended your swap be at least the same size as your installed RAM.
Root (/) and swap are separate partitions, but you can have root on logical partitions in linux. You can have /, /home & swap on logical partitions inside an extended partition. You can create as many logical partitions inside an extended partition so long as the space you allocated to the extended partition will allow it. See here for very detailed info: [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by mostafa178 on 2009-08-15
Thanks everyone! Now I just need to know if the current Ubuntu (9.04) can read and write to the HFS+ Journaled partition.

---

### Post by presence1960 on 2009-08-15
```
It is easiest to always install Linux as the second (or last) OS. If you install it first, the multi boot often fails and you can only boot to one OS which turns out to be the last OS installed. Then you have to go in and repair the boot process... or, start all over again.
```

That is a myth about starting over again, it is very simple to restore booting to both OSs. When you install windows after Linux the only thing that happens is the windows bootloader overwrites GRUB on the MBR. Both installs are on the hard disk, all you need to do is this to restore GRUB to MBR so you can boot both again:

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
In #6 install GRUB to MBR using setup (hdx) where x is the number of your hard disk. remeber counting starts at 0. the first hard disk is 0.

here are some links to back me up:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by mostafa178 on 2009-08-15
Thank you. Can Ubuntu 9.04 read and write to the Mac OS X Journaled partition?

---

### Post by Partyboi2 on 2009-08-15
Ubuntu can read hfs+ to write to hfs+ you would need to turn of the journaling, which is not recommended.
> 
**Disabling journaling on your main OS X partition is not recommended however as journaling is an important feature of any filesystem that can prevent damage and data loss**:

[https://help.ubuntu.com/community/hfsplus](https://help.ubuntu.com/community/hfsplus)

---

### Post by mostafa178 on 2009-08-15
Is there a format that Ubuntu and Mac OS X can both read and write to, excluding FAT32?

---

### Post by raymondh on 2009-08-15
> **mostafa178 said:**
> Is there a format that Ubuntu and Mac OS X can both read and write to, excluding FAT32?

[http://ubuntuforums.org/showthread.php?t=976751](http://ubuntuforums.org/showthread.php?t=976751)

---

### Post by mostafa178 on 2009-08-15
Thank you!

---

