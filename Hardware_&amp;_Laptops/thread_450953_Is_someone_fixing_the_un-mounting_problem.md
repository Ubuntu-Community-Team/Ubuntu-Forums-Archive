---
title: "Is someone fixing the un-mounting problem?"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by Afkpuz on 2007-05-21
This thread is actually 2 questions.

1.)   I, as well as many other people are having trouble ejecting usb drives.  I have a 120 gb usb hard drive that worked great with the past 2 versions of ubuntu.  The "eject" function worked fine with this particular drive in both dapper and edgy.  However, I'm unable to eject this drive in fiesty.  It tells me "unable to eject drive" and then it opens the drive in a browser window.  I figure that this would be an easy fix since it worked in previous versions, but I'm no developer.  I've seen than many other people are having this problem and I'm just wondering if we're working on this problem.  


2.) Also, I've been trying to format said drive and am unable to find a graphical way to do it.  In dapper, I could select system>administration>drives and format to my hearts content.  Where has that feature gone in fiesty?

---

### Post by jerrylamos on 2007-05-21
> **Afkpuz said:**
> This thread is actually 2 questions.

1.)   I, as well as many other people are having trouble ejecting usb drives.  I have a 120 gb usb hard drive that worked great with the past 2 versions of ubuntu.  The "eject" function worked fine with this particular drive in both dapper and edgy.  However, I'm unable to eject this drive in fiesty.  It tells me "unable to eject drive" and then it opens the drive in a browser window.  I figure that this would be an easy fix since it worked in previous versions, but I'm no developer.  I've seen than many other people are having this problem and I'm just wondering if we're working on this problem.  


2.) Also, I've been trying to format said drive and am unable to find a graphical way to do it.  In dapper, I could select system>administration>drives and format to my hearts content.  Where has that feature gone in fiesty?

1.) 7.04 has a bunch of new code doing SCSI simulation of IDE, SATA, CD's, USB, ... and is not as stable as Dapper or Edgy.  I don't have a USB hard drive and suggest doing some searching on some keywords that might be productive.

2.) Safest way I've found (!) to format USB drives is Gparted.  It might be in your System, Administration menu, or you could bring up CD Live with any of the Ubuntu versions.  There's a little box in the upper right corner so you can select your USB drive.  You should be able to unmount it, then select whatever format you want, say ext3.  Do note what address Gparted calls it, /dev/s???.  and format the drive.  You're done unless you like a volume label like I do:

Quit Gparted, then in Applications, Accessories, Terminal do 
sudo e2label /dev/s??? casper-rw
where the casper-rw is any volume label you'd like.  That's the label for CD Live "persistent" on 6.06 and 6.10 (persistent is broken on 7.04).

---

### Post by ramjet_1953 on 2007-05-22
If you follow this thread it will show you how to fix it:

[http://ubuntuforums.org/showthread.php?t=418688&highlight=evilc](http://ubuntuforums.org/showthread.php?t=418688&highlight=evilc)

Regards,
Roger :cool:

---

