---
title: "Unable to install on USB HD"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by tadiv on 2007-02-18
I have the ubuntu 6.10 CD and had no issue loading the OS to a desktop machine.  To have some portable opportunity to work with this OS, I booted the CD on my laptop.  It seemed to be okay, but I have been unsuccessful installing the OS to a Seagate 60 GB USB HD.  The install fails while the partition SW is attempting to create the ext3 file system...  I have tried three times and each time the generation of this FS has failed...  Any ideas?  The HD works fine in WIN-XP, but I actually just want it to ne a drive that contains ubuntu...

---

### Post by tadiv on 2007-02-18
Okay - so it looks like I have wrestled this problem down.  It looks like the issue was that for whatever reason, Ubuntu did not like trying to write to the USB HD at the USB 1.1 slow rate.  I spent some $$ and got a PCMCIA card that has USB 2.0 ports - I was able to use these ports to install onto the USB HD.  As luck would have it, I can't boot from that setup, however, I can boot with the HD on the USB 1.1 ports.

SO - it's not as fast as it might be, but it is working...

Tom

---

