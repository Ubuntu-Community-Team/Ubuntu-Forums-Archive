---
title: "ECS A780LM-M2 Motherboard problems."
date: 2013-10-10
forum: Hardware
---

### Post by DarkDancer on 2013-10-10
I have (for a friend) the above mentioned motherboard and while Ubuntu 13.04 will install just fine, when It tries to go to Grub, there is an error. I unfortunately do not remember the exact error message (I will be at his house later and will post it) but it is something about illegal writing to a certain sector (0?). I have searched the error and while I find other people with it, no one seems to know how to fix it. Any one seen this error and have any cluie how to resolve this?

---

### Post by DarkDancer on 2013-10-10
Ok, so here it what I tried. Because Saucy is about to be released,  I downloaded the Beta, hoping that that might fix the issue. No. So here are the Errors I get.

Error: Attempt to read or write outside of disk 'hd0'.

Also sometimes it will give this:

Error: failure reading sector 0x197d20 from the from 'hd0'
Error :You need to load the kernel first


Any ideas?

---

### Post by DarkDancer on 2013-10-17
Any one? Any one? Bueller, Bueller?

---

### Post by DarkDancer on 2013-10-31
No clues at all?

---

### Post by DarkDancer on 2013-11-07
Awesome. I wseem to have stumped everyone.

---

### Post by oldfred on 2013-11-07
Those seem to be two separate unrelated errors. Or possibly hard disk corruption or failure.

Outside of disk usually is a partition table error that must be fixed before anything works, or I would not expect you to even get to a kernel error.

And kernel error is often defective download that did not install correctly.

Just to confirm that drive is ok, what does Smart Data status show. You will find it in Disks or Disk Utility depending on version, click on drive and on right side is Smart Data. It can run a lot of tests, but I only know passed or green is good and just about anything else is new drive.

---

### Post by DarkDancer on 2013-11-07
Yay a response! Thank you! I'm using Puppy, how do I get to Smart data from there? I may not be able to respond to your response as it is a friends computer and I only come once a week. I have googled the errors and see them, but no one seems to know how to fix it.....

---

### Post by oldfred on 2013-11-07
I have not used Puppy for a while. Not sure if it has the command line version or if you can install it?

 gsmartcontrol
smartmontools - lists harddrive detail info
smartctl and smartd
[http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T)
sudo smartctl -d ata -a /dev/sda -T permissive
Disk Utility screen shots
[http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/](http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/)

---

