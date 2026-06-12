---
title: "cannot resize Windows partition: dual boot"
date: 2006-01-13
forum: Installation &amp; Upgrades
---

### Post by buldir on 2006-01-13
Has anyone had a scenario where they couldn't resize a preexisting Windows partition? My dad just tried to install Breezy on his Windows box. He has 1 160 GB drive, with Windows XP on the first 60 and data on the last 100. He was hoping to resize the 60 GB partition down to 30 and put Breezy on the free remaining 30, but he said the installer "wouldn't let him do it". I'm not sure what that means exactly. Should he have defragmented his 60 GB partition prior to installing Linux? He said he followed the instructions at [https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo) to a "T". Any thoughts?

---

### Post by hillbilly on 2006-01-13
hey buldir, could you post some more info. Was any error being thrown. What program did your dad use to partition ? 
It would help us to help you.

---

### Post by GrayMiata on 2006-01-13
Pehaps I can provide more information than what my son can provide.  I was using the ubuntu 5.10 install bootable CD and the partition program that came with it. When I tried to resize the 60 GB primary partition, NTFS, on a 160 GB HDD, to create some free space, nothing occurs, not even an error message.  The free space is simply not created and the original 60 GB primary partition remains as is.  I am following the instructions from the ubuntu documentation to install a dual boot with Windows XP Professional already installed.  With the ubuntu partition installer I can create free space on the 100 GB logical partition, and can proceed to install ubuntu which is completed successfully.  I reboot when prompted and I get an error message after the computer tries to load Grub, Error 2, then the system halts.

From what I was told, Grub needs to be on the primary partition.  Trying the command: grub-install /dev/hda at the ubuntu boot prompt, I receive the error cannot find the kernal grub-install.

Using the system resuce CD as recommended in the Windows Dual Boot How to instructions, I tried to resize the primary partition to create free space, but I received an error message: Filesystem check failed. Totally 1 cluster accounting mismatches.

Are there any suggestions from experts?

Thanks

---

### Post by GrayMiata on 2006-01-13
One other point I need to make.  I did perform the defrag on both partitions before I tried to install ubuntu.

GrayMiata

---

### Post by aysiu on 2006-01-13
I would recommend [using DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142) to resize Windows and then install Ubuntu.

---

### Post by GrayMiata on 2006-01-14
I eventually figured out what the problem was.  The way my hardware was connected prevented the successful installation of the grub loader in the MBR(?).  The hard drive was not directly connected the the motherboard, but to a SIIG UltraATA 133 PCI add-on card and the ATAPI devices connected directly to the motherboard.  I remembered, late yesterday, when I had this specific hookup, even WXP Pro would not install.  So this morning I rearranged the connections to have the HDD connected to the primary IDE port while two of the ATAPI devices, the CD & DVD writers, were connected to the secondary IDE port on the motherboard.  A DVD-ROM drive is connected to one of the two ports on the SIIG PCI card.  The writers need to be on the motherboard ports otherwise they won't write to disks properly.  So with that, I re-ran Ubuntu install but still could not re-size the 60 GB primary partition, (free space not created), even using the gtparting software on the linux system rescue CD, same error message "Filesystem check failed Totally 1 cluster accounting mismatches".  So I tried to create the free space (30 GB) from the 100 GB logical partition and the swap partition, which worked ok, and the installation of Ubuntu completed successfully and even started up finished loading and even updated a bunch of programs.  It seems the Linux OS works ok.

The biggest test was starting WXP after the linux install.  The only problem I saw was when WXP tried to start, it ran chkdsk on the remaining 70 GB logical partition to correct some errors.  If that never happens again all should be fine.  It appears all files and programs are intact, so far.  I re-ran defrag again to make sure.

Thanks to all who offered help.  It is difficult to pinpoint a computer problem without knowing specific details on the hardware and connections.

GrayMiata
:p

---

### Post by hillbilly on 2006-01-17
Way to go graymiata.

---

### Post by gojohnniegogo on 2007-12-19
Hi, first time user trying to install Ubuntu 710 on a standard 32bit AMD Machine. I watched a few videos on how to install a dual boot with Windows XP, and the option to resize the partition as seen in the videos just isn't there! I have only a 40GB HDD, of which about 50% total has been used with Windows - all my music and video, etc is on my external 320GB Seagate. Can anyone help please?

---

### Post by Pumalite on 2007-12-19
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
Use Gparted Live CD to resize your XP partition.

---

### Post by gojohnniegogo on 2007-12-21
Sorted now, and happily running Ubuntu :)

---

