---
title: "Installing Vista and Ubuntu (and Fedora) with Windows Boot Manager"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by abhinavk on 2009-01-02
I have found a way to install Ubuntu (and Fedora) on a Vista machine while keeping the Windows Boot Manager. The reason behind having Windows BM because the windows users find it awkward when they see a GRUB menu after installing Ubuntu. Even many first ever see a boot menu, after they install Ubuntu.

In GRUB, they are confused with lots of ubuntu........generic kernels....

So what should we do now...
There are too options...

[LIST=1]
[*]Use the Windows Boot Manager with streamlined options
[*]Request Ubuntu developers to use GRUB2 with a graphic boot menu
[/LIST]

We couldn't apply the second ourselves. So I am here with first choice.......

1. I presume that you have Windows Vista installed on C:, if not install it first.

2. Insert your Ubuntu CD or DVD in the drive, and boot from it to begin setup. Choose "Install Ubuntu" from the bootable menu. Or Double-click the "Install" icon on the desktop to get started, if you have already started Ubuntu right from the live CD.

3. Follow the setup prompts until you get to a screen asking you for your preferred method of partition your hard drive. Choose "manual" at this point so you can configure your dual-boot exactly as you need it.

4. Find some free space on the drive (or resize/move existing partitions around to make some) and create a new partition there. Choose "ext3" as the filesystem type and "/" as the mount-point. (You can choose other filesystem such as ext2, reiserfs etc but ext3 is recommended. Note you cannot install to a FAT32/NTFS, on these filesystems, you won't have "/" mount point available). Also create a SWAP partition of size >256 MB with "/swap" as mount point.

5. Now you have come to the most important step, telling ubuntu where to install GRUB. On the Ready to install page, click the lonely button "Advanced..."

6. Now is the time to tell Ubuntu that we don't want GRUB installed to the system bootloader (MBR). Instead, we're going to have Ubuntu install GRUB to its own partition. The default option is (hd#) where "#" is the number of the drive your installing Ubuntu to...

7. The (hd#) means that it is installing to MBR (Master Boot Loader where the BIOS seeks for an OS/Boot loader) of disk #. In the current configuration of your pc, windows boot loader of vista is installed on your MBR. While (hd#,x) refers to partition x of disk #, thus installing GRUB to boot sector of the partition and not the MBR of disk.
Edit (hd#) to (hd<hard drive id>,<partition id>)

To find out which is the correct partition and what is its id,read the section info note below...

NOTE:
[SIZE=1]
**In the Boot Loader install prompt**

(hd#,X) where "hd" means hard disk and "#" means disk id (begins from 0) and "X" means partition id (also begins from 0)
while a (hd#) refers to MBR of disk #.

eg
(hd0) means MBR of first disk
(hd0,0) means first partition of first disk
(hd0,1) means second Partition of first disk
(hd1,0) means first partition of second disk

**In the partitioner (gParted) page**
There are other different references to drives in the setup too... (specially in the partitioner)
like sd$#(SATA) and hd$#(ATA/IDE) but in ubuntu both are merged in sd$#

on the gparted, you will see drives in /dev/sd$#
/dev/sd$# where "$" is the drive id in small alphabets (begins from "a"), "#" means the partition id (also begins from "1")

eg
/dev/sda means MBR of first disk; same as (hd0)
/dev/sda1 means first partition of first disk; same as (hd0,0)
/dev/sda2 means second partition of first disk; same as (hd0,1)
/dev/sdb1 means first partition of second disk; same as (hd1,0)
[/SIZE]

Enter a valid value as per your drive configuration. (You can enter the value in either of the formats)

In my case, I had created a new second partition for Ubuntu (/dev/sda2) apart from Windows partition (/dev/sda1), so I had to enter either **(hd0,1)** or **/dev/sda2** that refers to boot sector of the ubuntu partition.

Now you are good to go. Continue the installation and Get a cup of coffee.

8. Now boot to Vista from GRUB menu and install a program called [EasyBCD]("http://neosmart.net/downloads/software/EasyBCD/EasyBCD%201.7.2.exe") (supported and recommended by Microsoft Corp).

9. Open EasyBCD and click "Add or Remove Entries".

10. Click the Linux Tab and enter the following values...

Type  = Grub
Name  = Ubuntu (it's ur choice man....)
Drive = <choose the drive, you have installed Ubuntu to...)

Keepin mind that in Windows drives start from 0 and partitions start from 1. partition 0 refers to MBR.

[SIZE="1"]
therefore,
First partition of first disk ie
**(hd0,0)** or **/dev/sda1** in Linux is **Drive 0, Partition 1 in Windows**

MBR of first disk ie
**(hd0)** or **/dev/sda** in Linux is **Drive 0, Partition 0 in Windows**
[/SIZE]


11. Click Add Entry and all is done.....

**For Fedora**
Install like the normal way except the boot loader on a boot sector not on the MBR. Then add entry for Fedora in EasyBCD.

**If you have already installed Ubuntu before Vista.**
Install Vista. It will replace the GRUB with Windows Boot Manager. Then add the Ubuntu entry in EasyBCD to the Vista Boot Manager.

---

