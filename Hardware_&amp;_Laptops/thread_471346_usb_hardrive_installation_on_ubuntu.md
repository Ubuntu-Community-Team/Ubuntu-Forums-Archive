---
title: "usb hardrive installation on ubuntu"
date: 2007-06-11
forum: Hardware &amp; Laptops
---

### Post by rob-n on 2007-06-11
this is an update on my first post which i can't find. i have located by using fdisk -l the usb
drive but it is not accessible. my drives including the new 40g internal are all labeled sd
as in sda for the internal drive, sdb for the 160g usb drive and sdc for my 2g mp3 player.
i used qtparted to partition the 160g drive and thats where i'm stuck. i'm using ubuntu,the
latest version no other os has been on the drives.

thanks rob-n

---

### Post by grahams on 2007-06-12
How are you trying to access the disk?

It sounds like you have partitioned the disk, have you created a filesystem?

If your partition is at /dev/sdb1 you would need to run something like :
sudo mkfs -t ext3 /dev/sdb1
This will create an ext3 file system on the partition (ubuntu default).

You may find the disk gets auto-mounted if not you should be able to manually mount it:

Create the mount point 1st
sudo mkdir /media/mydisk (or anywhere else you'd like to mount the disk)
then mount it
sudo mount /dev/sdb1 /media/mydisk
if everything went well type 'df' and you should see your 160GB partition.

---

### Post by rob-n on 2007-06-12
thank you.
i followed your directions and now i have my external drive on my desktop.
the drive i bought is supposed to have a one touch backup but as the cd is for
windows and mac only it dosn't work. the drive permission is for read only.
ihave tried sudo fdisk -l followed by df -h and got nothing. perhapes you have
an answer for this as well. i am determined to use linux only for ever and i'm
gradually leaning how to use the command line

---

### Post by grahams on 2007-06-12
Sounds like you're making progress :)

If you've mounted the disk, but you can't write to it as a normal user but can as root or when using sudo, it's likely that you just need to edit the permissions of the mount point. 
'sudo chmod 777 /media/mydisk' should allow every user read * write access to the disk.

If want to have the disk mounted everytime you boot you can edit the /etc/fstab file. 

Check out the great instructions at [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by rob-n on 2007-06-13
they say you can't teach an old dog new tricks. well this old dog finally leaned a new trick.
the answer was in front of me all the time and i just didn't get it. for some reason i got stuck
on mounting the disk automatically whenever i boot up. then i became clear to me. the disk
was mounting ever time i booted. all i needed was that one line from your post.
sudo chmod -R 777 /media/disk. and reboot and now i have the power.

once again thank you for all your help. other things i looked at while wandering aimlessly about
have other answers that i won't need to bug others about.

rob-n

---

