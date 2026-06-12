---
title: "Help with ext3 slave drive dir issues"
date: 2009-12-21
forum: Hardware
---

### Post by Fuzzy-Mark on 2009-12-21
I'm pretty much a newbie when it comes to command lines. I pieced together an old desktop, 1.2 ghz, 40g hd, 512 ram. I added a second 40g hd and set the jumpers on both drives accordingly. I installed 9.04 and was able to remove partitions on the slave during set up but it was not formatted. The drive did not appear in "places" or "computer". I followed some tutorials to partition the drive, format with ext3, create a dir, and edit fstab. Here are those tutorials:

[http://www.ehow.com/how_5068221_format-linux-hard-drives.html](http://www.ehow.com/how_5068221_format-linux-hard-drives.html)
[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

According to the terminal, the slave (sdb1) is mounted but I still can't see it in "places" or "computer". This computer is for my sister and I need the drive to work with the gui. I found the dir I created (/mnt/galaxy) in the mnt folder of the main filesystem. I don't see where I associated the new dir with the slave drive until the fstab edit. Is this right? How can I get the drive or the dir "galaxy" to show up in the "places" menu for all users? 

I have been searching all around and can't seem to figure it out, any help is greatly appreciated.
Thanks.

---

