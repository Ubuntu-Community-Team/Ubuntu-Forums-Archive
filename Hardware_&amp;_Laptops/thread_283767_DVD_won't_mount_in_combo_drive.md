---
title: "DVD won't mount in combo drive"
date: 2006-10-24
forum: Hardware &amp; Laptops
---

### Post by linuxgrrl on 2006-10-24
hi,
I have a CD/DVD combo drive that can read and write CDs but chokes on DVDs.  Under breezy, I got this error
> Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: I could not determine the filesystem type, and none was specified
Error: could not execute pmount

I upgraded to Dapper, and now the error is simply > "I could not determine the filesystem type"
Here is my /etc/fstab if it helps:> proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda3 /boot ext3 defaults 0 2
/dev/hda5 none swap sw 0 0
/dev/mediavg/videolv /var/video xfs rw,noatime 0 0
/dev/mediavg/photoslv /var/photos ext3 rw,noatime 0 0
/dev/mediavg/musiclv /var/music ext3 rw,noatime 0 0
/dev/hdc /media/cdrom0 auto user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

thanks for any suggestions!
Mary

---

### Post by linuxgrrl on 2006-10-27
anybody?

---

### Post by linuxgrrl on 2006-11-16
OK, I finally got an answer to this in LinuxQuestions.org ... did two things per their advice:
1.  enabled DMA using the "hdparm" command (type "man hdparm" for more information)

2. changed the permissions on the *parent* folders of the files I wanted to write to DVD. Not sure why that was necessary.

Now it works!  Trying k3b instead of the nautilus burning utility was also helpful, as it provided the detailed error messages that clued me in about the permissions problem.

---

### Post by Caveira2099 on 2007-01-12
Just to clarify for all those who are still facing this issue, I was having the same issues with both Ubuntu 6.10 and Fedora Core 6.

Solved it after reading this post:

First, enable DMA on Combo drive:

$ sudo hdparm -d1 /dev/hdc

After, editing /etc/fstab:

$ sudo gedit /etc/fstab

Changing the line of the cd/dvd-drive:

From: /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
To::::: /dev/hdc        /media/cdrom0   auto user,noauto     0       0

I have also installed ivman on a desperate move, but I don't think this had any influences.

Thanks.

---

