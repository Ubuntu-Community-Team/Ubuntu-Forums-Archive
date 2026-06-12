---
title: "Adding hard drive in Dapper - need help"
date: 2006-05-24
forum: Hardware &amp; Laptops
---

### Post by hardbop200 on 2006-05-24
Hello,

I need to add a second hard drive to both of my machines (one uses SCSI, the other uses IDE).  I need this drive for recording audio, so if I ever have to reinstall, I can keep my audio and MIDI projects untouched.  Here's my problem:

I've successfully found the hard drive and created a partition on it.  I've also successfully formatted it with the ext3 filesystem.  My question is:  how do I add it to /etc/fstab so that:  1)it is mounted automatically at every boot; 2)my user can freely write to it without having to sudo each time?  I want the drive/partition to be called /data.

For example, I do not know how or where to make the mount point.  Initially I added it to /media/data.  I added this to the fstab:

```

/dev/sdb1  /media/data ext3 rw,users,auto 0 0

```

but it doesn't seem to work.  I can mount it, but it isn't mounting automatically, and I *still* can't freely write to it without sudo'ing. 

Can someone point me to what I'm doing wrong?

Thanks!

---

### Post by scion4 on 2006-05-24
Hi the easy way is to go to the KDE system settings in the menu, select Disks and Filesystems from the System Administration Section.

Click administrative mode button and enter root pass.
You should be able to see in the GUI your added USB hard drive and will be disabled.
You need to set this up, select the drive from the list.
Go New >>
Type: ext3 - Third Extended FS
Mount Point: /media/data/
Device: (as displayed in the list you orginally choose HDD from) /dev/sdb1/ 
Select enable at startup and writeable.
Mount permission: any user may enable/disable anytime

This setup writes this entry into fstab for you and has worked great for all of my mounts.

---

