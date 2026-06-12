---
title: "Adding hard drives"
date: 2004-10-12
forum: Hardware &amp; Laptops
---

### Post by corleone on 2004-10-12
Hello, I just installed Ubuntu a couple days ago, and before I installed it I unplugged my other hard drives, just to make sure there was no way to screw them up as I am a complete linux nub... anyway, now I want to use those hard drives.  I plugged both in, and I can see the computer detects them on the startup, but once Ubuntu has started I go to "disks" and they are not there.  What do I need to do to get these recognized by Ubuntu?  Thanks.

---

### Post by Mindstab on 2004-10-12
my guess would be you'll still have to add an entry in /etc/fstab

$ sudo $EDITOR /etc/fstab

tell me how it turns out
i'll adding a hard drive to my girl fiends ubuntu box next weekend

---

### Post by corleone on 2004-10-12
Hrm, I don't know what to put under any of this (told you I was a nub).  What do I put under &lt;file system&gt; &lt;mount point&gt; &lt;type&gt; &lt;options&gt; &lt;dump&gt; &lt;pass&gt;?   Oh and what do all of these things mean?

---

### Post by Anonymous on 2004-10-12
Hi! ^_^
Well I think  you have to take those steps:
Linux systems give names to devices attached to the ide channel as follows:
Primary Master: hda
Primary Slave: hdb
Secondary Master: hdc
Secondary Slave: hdd
Assuming you have mounted your hdd as Secondary Master (hdc) and it has just one partition (this way the partition is the first and the device is called hdc1):
1) Create a mount point somewhere in your filesystem, assume /mnt/hdc1 with this command:
sudo mkdir /mnt/hdc1
2) edit /etc/fstab:
sudo nano /etc/fstab
3) Add a line like this:
/dev/hdc1 /mnt/hdc1 auto defaults,user 0 0
4) Save the file and exit pressing ctrl+x confirming with y and return

Now you can test it rebooting...

P.S. I made a script that automatically updates during boot the fstab accordingly to which devices are plugged to ide channels, if you want I can post it, you havo to install it as an init script.

---

### Post by corleone on 2004-10-12
Ah, got it figured out,  Thanks for the help!

---

### Post by nerotje on 2004-10-21
[quote=Tasu]...

P.S. I made a script that automatically updates during boot the fstab accordingly to which devices are plugged to ide channels, if you want I can post it, you havo to install it as an init script.[/quote]
I'm still interested in it to how it works.
I need a loke alike for detecting and mounting external USB drives.
It has 4 partitions in an extended partition, to be exact.
No primary and no space left to add it.

---

