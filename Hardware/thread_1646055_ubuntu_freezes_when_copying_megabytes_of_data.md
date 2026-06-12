---
title: "ubuntu freezes when copying megabytes of data"
date: 2010-12-15
forum: Hardware
---

### Post by EntropyReduction on 2010-12-15
Apologies if I'm posting to the wrong place.  I'm a ubuntu newbie.

 Just installed 10.10 on an  acer aspire 5101AWLMi with a replacement Seagate 320gb Momentus 7200.4 HD.

  Install went flawlessly.  I added a few partitions, one meant primarily for data to be shared, eventually, with a win VirtualBox install, and across LAN to a couple of win machines. 

 Installing all sorts of software via ubuntu software centre, no problems, or none that a bit of googling couldn't solve. 

 To get started, began copying data from a memory stick to this partition; went ok for a while, then Ubuntu froze solid; no input recognised, no way out (that I know of) except forcing a power off and rebooting.  This happened repeatedly.  Proportion of time the partition was hosed, had to reformat it.   

 I tried an NTFS format, then FAT, then EXT4; all the same result.

 No predictable amount of data transferred before a freeze; sometimes a few hundred MB, sometimes much less.

  I was beginning to think &quot;hardware problem&quot;; but a response to a query on a sort-of-similar problem suggested dropping back to a previous kernel version (I had updated from 2.6.35-22 to 2.6.35-23 immediately after install).  So I booted from 2.6.35-22 (after a bit of messing about with


      sudo update-initramfs -u -k 2.6.35-22-generic

 (What's that about?  Nevermind, it worked).

 Presto.  Problem gone.

 So: is that a bug?  Did I do something wrong?  If not, should a report a bug on kernel 2.6.35-23?

 Now wildly impressed with silent magic that somehow means I can browse my ext4 partition from a win machine on LAN. 

 Many thanks for any help.

 

 Alan C

---

