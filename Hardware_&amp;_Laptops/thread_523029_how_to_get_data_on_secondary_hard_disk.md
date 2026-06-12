---
title: "how to get data on secondary hard disk?"
date: 2007-08-11
forum: Hardware &amp; Laptops
---

### Post by sigurdkaare on 2007-08-11
Hi everybody! please help me wiht this one!

I have in GNOME partion Editor deleted all data on my secondary hard disk and created a ext2 partition. I need the secondary hard disk 'cause my main hard disk is only a 80 GB

All looks fine, but I can't  load data on the disk. It is mountet.

Why is that? Do I need to link to my home folder ? How do I do it? 

Sigurd

---

### Post by Scunizi on 2007-08-11
Instead of ext2 you should be using ext3.  It has journaling and is safer for your data.  You may have to add a line in /etc/fstab for your machine to recognize the drive correctly.  Also in /media you'll have to create a directory to list the contents of the drive.. Whatever you name the directory will have to be referanced in the fstab line.

---

### Post by sigurdkaare on 2007-08-12
Hi, 

now I made it ext 3

But I don't understand the rest of the explanation. I'm quit new to unbutu.

"You may have to add a line in /etc/fstab " - I found the file:

- It is read only file. How do I get allowed to make changes in it?

- What line should I add?  What information on the harddisk should I add, I where do I find it, and how should I add it?

"Also in /media you'll have to create a directory to list the contents of the drive" - there is already a directory called "disk" that links to the harddisk.

I'm sorry, but I just don't understand the explantion. Is there a way for linux dummies to do it?

Sigurd

---

### Post by Scunizi on 2007-08-12
Here are a couple of referances to help you out.  Remember, in Ubuntu to gain root or administrator privilidges you have to preface a command in the terminal with "sudo".  So to edit /etc/fstab you would type "sudo nano /etc/fstab" or "sudo gedit /etc/fstab".  Nano and gedit are two different text editors.  You'll find gedit easier to move around in.  Nano works well when you need to rescue the system and don't have a gui.

Here's a couple of links..  
[http://doc.gwos.org/index.php/Understanding_fstab](http://doc.gwos.org/index.php/Understanding_fstab)
[https://help.ubuntu.com/community/Fstab?highlight=%28fstab%29](https://help.ubuntu.com/community/Fstab?highlight=%28fstab%29)

Here's some examples of an fstab file.  You'll probably notice that the only line that resembles what you have in Feisty's fstab is the line that begins with UUID.  Previous versions of Ubuntu used a different method as represented by /dev/sd? or hd?

> /dev/sda14 /mnt/zen ext3 defaults 0 2 
/dev/sda1 /media/usb auto user,rw 0 0 LABEL=data /mnt/usr_data ext3 auto,users,rw 0 0 UUID=fab05680-eb08-4420-959a-ff915cdfcb44 /media/flash vfat user,rw 0 0 
/dev/disk/by-id/usb-IOMEGA_ZIP_250_059B00301400B0F1-part4 /mnt/zip vfat user,noauto,umask=077 0 0 
/dev/hda1 /mnt/windows ntfs auto,ro,users 0 0 
/dev/hda1 /mnt/windows ntfs-3g users,auto,uid=1000,gid=100,umask=007 0 0 
/dev/sdb4 /media/zip vfat users,noauto,uid=1000,gid=100,umask=007 0 0

Here's my fstab file.  It's kinda large since I have Dapper, Ubuntu Feisty, Kubuntu Feisty and Debian Etch installed.  All the lines with a "#" in front of them are not read by the computer.  They are "commented out"  that's what the "#" does.  I use the # to make comments within the fstab file for things that I have going or just to remind me where I've put different things.  

Another thing of note, drives are designated as sda? or hd? .. like sda1, sdb1, hda1, hdb2.  S is for SATA drives, the a,b,c etc is to designate different physical drives, the number at the end designates the different partitions within the drive.

I hope this helps!

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb3       /               reiserfs notail          0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda2	/media/sda2	reiserfs rw.user	0	1
/dev/sda3	/media/sda3	reiserfs rw,user	0	1
/dev/sda5	/media/sda5	ext3	defaults,rw,user	0	1
/dev/sdb1       /media/sdb1     ext3    rw,user	0	1
/dev/sdb5       /media/sdb5     vfat    defaults,utf8,umask=007,gid=46 0       1
/dev/sdb6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/hda1	ext3	defaults,rw,user	0	1
/dev/hda2	/media/hda2	ext3	rw,user	0	1

#/dev/hda1	/media/hda1	vfat	user,auto,fmask=0111,dmask=0000
#/dev/sda2	/media/sda2	ext3	rw,user	0	1
#/dev/hda5	/media/hda5	ext3	rw,user	0	1
#/dev/sdc1	/media/ipod	vfat	user,noauto,umask=000	0	0

#//ip-or-hostname/MUSIC /media/music cifs	user.noauto.credentials=/home/joey/.smbcredentials.uid=joey 0	0

#sdb1 Linux		unknown
#sdb2 Extended		unknown
#sdb3 is Dapper root/home ReiserFS
#sdb4 non-existant (Extended partition)
#sdb5 is Vfat Trans	Fat32
#sdb6 is swap		swap

#sda1 is XP		NTFS
#sda2 Ubuntu Feisty	ext3?
#sda3 Kubuntu Feisty	ext3?
#sda4 Extended		unknown
#sda5 Linux		unknown
#sda6 swap

#hda1 Data		Ext3
#hda2 Data		Ext3

```

---

