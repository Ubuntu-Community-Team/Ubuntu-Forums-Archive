---
title: "Extremely slow transfers after running Deluge BT"
date: 2008-07-27
forum: General Help
---

### Post by jberquest on 2008-07-27
I have a system running Ubuntu Hardy, and have had a problem with slow transfers after leaving Deluge running overnight.  After a fresh format of the drive, transfers are about 35 MB/sec, but after running Deluge overnight, transfers crawl at 500KB/sec to a max of 3MB/sec.  Unmounting and reformatting the drive eliminates the slow transfer problem.  Where do I even begin to look to troubleshoot this?  The drive is a 250gig WD SATA drive, running on a  SYBA SD-SATA-4P pci adaptor.  Any suggestions?

---

### Post by icheyne on 2008-07-27
Are you sure it's not your ISP throttling your connection somehow? Have you tried another Bittorrent client?

---

### Post by jberquest on 2008-07-27
I'm sorry, I was unclear.  Disk to disk transfers are slow.  I am transferring files from /dev/sda1 ext3 to another disk, /dev/sdd1 ext3.

---

