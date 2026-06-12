---
title: "NTFS Disk not recognized by BIOS and wont boot but Ubuntu Live CD can see it"
date: 2013-04-10
forum: Hardware
---

### Post by pawaz on 2013-04-10
I have a problem whereby my disk which had Windows 7 32 bit wont boot. On boot up I get an error claiming that *there is no hard drive installed on the system*. A check in the BIOS also shows there is no hard disk drive. But when I boot with a Live CD or USB stick with Ubuntu I get to see my OS partition and Data partition and I have gotten a chance to back up all my data no problem.
After backing up I tried formatting the disk with Ext4 and installed Ubuntu to it no problem but again when I boot up I get the same problem of the system claiming that there is no disk present. Any one know what could cause the disk not to show on start up? 
Is there any utility which can fix such a problem?

---

### Post by oldfred on 2013-04-10
Welcome to the forums.

Operating systems whether Windows or Linux only see the devices the BIOS enumerate. So BIOS has to see it, but it may not show it as bootable? There also are BISO settings to lock devices, but then that is usually the opposite issue that it is seen in BIOS but not the operating system.

Post this.

sudo parted -l  
That is -el not cap I or num 1.

---

### Post by pawaz on 2013-04-11
Thank you for the reply. 
I kid u not BIOS doesnt see it and yet Ubuntu sees the disk. I dont know by which miraculous means this happened but thats the way it is. i have assembled many PCs in my day so I know what am talking about. 

anyways ***sudo parted -l*** gives me the following

Model: ATA TOSHIBA MK5055GS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 3      1049kB  84.9GB  84.9GB  primary  ext4
 1      84.9GB  216GB   131GB   primary  ntfs         boot
 2      216GB   500GB   285GB   primary  ntfs


Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: Can't have a partition outside the disk!


btw is there any way a malicious virus could have caused this? I wasnt running any antivirus in windows when this happened.

---

### Post by oldfred on 2013-04-11
Perhaps grub did not get installed or installed correctly.

I might try this first, your install is sda3, so change all sda5's in example to sda3.
       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by pawaz on 2013-04-13
I think its not so much a grub problem as I read online of people with HP Bios and Toshiba drives having the same problem of hard disks in perfect working order not showing up.
I have managed to boot into my old Windows 7 via grub that's on the main drive. 

I did this by having the Windows 7 installation disk in the CD drive and also a portable USB hard disk connected and somehow this makes it to boot even tho the main hard disk not being detected by BIOS is still persistent. But atleast I can get to use my Windows software. Even tho booting via this method doesnt work 100% of the time I will keep using this work around until I can get a new drive. 
am very thankful for your help Oldfred

---

