---
title: "How to best partition across disks?"
date: 2005-12-31
forum: Installation &amp; Upgrades
---

### Post by stuporglue on 2005-12-31
Essentially what I need to know is, how big do /boot, /tmp and /var need to be if they're on their own partitions?

I've got this old computer with several small disks, and no big ones. In all, I have plenty of space for Ubuntu, but I'm unsure the best way to spread the partitioning arround because I don't know how much is needed for /tmp /boot or /var.

The computer can't reliably boot from the SCSI disks, and can't handle a large boot partition. The disks are:

4.6 Gb SCSI (/dev/sda)
850 Mb SCSI (/dev/sdb)
425 Mb IDE (Primary Master) (/dev/hda)
CDROM (Secondary Master) (/dev/hdc)
I have a couple of 1 and two gig IDE drives I can stick in there if needed. 

I know I need /boot as one of the first partitions on /dev/hda. With that requirement, and the info above, does this look reasonable? Will /tmp or /var have enough room? 

/dev/hda
   /dev/hda1   50 Mb  /boot
   /dev/hda2   200 Mb /var
   /dev/hda3   175 Mb /tmp

/dev/sda
   /dev/sda1   4.2 Gb /home   
   /dev/sda2   400 Mb swap

/dev/sdb
   /dev/sdb1   850 Mb /


Thanks a bunch! By helping with this problem, you're helping give a computer to a student who doesn't have one (stuporglue.org), and spreading linux further. :-)

---

### Post by HarryMangurian on 2005-12-31
[http://www.hypermicro.com/product.asp?pf_id=HDSE122](http://www.hypermicro.com/product.asp?pf_id=HDSE122)

---

