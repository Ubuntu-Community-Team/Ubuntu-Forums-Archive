---
title: "dvd drive does not see rewritable or blank disc"
date: 2008-12-17
forum: Hardware
---

### Post by Ant68 on 2008-12-17
Hello,
I have a desktop computer with a DVD player RW (there is a second one but it is not used). It read ok (I have set up ubuntu from it)?

I would like to copy a .iso file from the computer to a DVD disc. but when I use CD/DVD creator it asked for:[B]
Insert a rewritable or blank disc[/B]
Please put a disc, with at least 2.3 GiB free, into the drive.  The following disc types are supported:
DVD+R DL, DVD-R, DVD-RW, DVD+R, DVD+RW

I insert a 4.7GB disc in the driver but I get nothing back. 


[U]/etc/fstab: static file system information.
[/U]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1948d24d-a767-490d-9d69-e513ef76c0ad /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d19b101d-8f99-4e9f-b78a-07fab9bdd5c1 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


When I try to accces (click on) the content (e.g. music) from the same DVD player: Places > Audio CD (was CE+RW / DVD+-RW Drive). It shows:
Could not open location 'cdda://scd1/'
Failed to execute child process "sound-juicer" (No such file or directory)

When I try to accces the drive with the empty DVD in: Places > CE+RW / DVD+-RW Drive. I get nothing back.

It is like it does not pick up there is a DVD ready to write on in the drive... 

What should I do?

---

