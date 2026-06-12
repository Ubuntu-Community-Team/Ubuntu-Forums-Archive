---
title: "How do I merge hard disk partitions using Gparted?"
date: 2012-08-02
forum: Hardware
---

### Post by amadeuslin on 2012-08-02
Hi,

I use Ubuntu 12.04 on Hp-pavilion dv6-6050se laptop. I have partitioned my 500 GB hard-drive into 5 partitions using Gparted.Now I want to merge two partitions(empty) to create a new one.

Can you help me?

---

### Post by drmrgd on 2012-08-02
First be sure that you've backed up anything you really value.  Any partition altering always has the possibility (however remote!) of failing and causing data loss.

You need to reboot from either the Ubuntu Live CD or you can create a Gparted Live CD for this purpose if you prefer ([http://gparted.sourceforge.net/livecd.php/](http://gparted.sourceforge.net/livecd.php/)).  Once you're in a live session, you just need to delete the partitions that you don't want to make them unformatted, and then expand the size of the partitions you do want to take up that unformatted space. It's pretty self explanatory once you're in there.  Here's a tutorial, though just in case:

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Once you've got things how you want them, then just click the apply button for Gparted to start performing the operations.  Depending on what you're doing and how much data you have, it could take a while to run.  So, if this is on a laptop, be sure you're plugged in, as a power failure from a dead battery is going to cause you some grief! 

Hope that helps!

---

