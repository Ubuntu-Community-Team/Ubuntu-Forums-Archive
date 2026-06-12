---
title: "Ubuntu doesn't load on my Lenovo X61t"
date: 2007-07-21
forum: Hardware &amp; Laptops
---

### Post by Chin Strap on 2007-07-21
Hi,

I have an X61 tablet, and no cd-rom drive, so I installed Feisty Fawn using an external USB enclosure with a cd-rom drive in it.  The live cd loads just fine, and I'm able to complete the install fine.  But when I reboot and try to log into Ubuntu, I get this:

ata1: port failed to respond (30 secs, Status 0x80)
ata1: COMRESET failed (device not ready)


and it just repeats those two things a bunch of times and never progresses beyond that.  

I've tried reflashing my cd-rom drive, no help. Unplugging the cd-rom drive, no help.

Anyone have any ideas?

---

### Post by drocko on 2007-07-21
Hey,

I'm also on an x61t! Have you changed the SATA settings in the BIOS to compatible mode? Seems to me like this should do the trick for you.

---

### Post by overdrank on 2007-07-21
> **Chin Strap said:**
> Hi,

I have an X61 tablet, and no cd-rom drive, so I installed Feisty Fawn using an external USB enclosure with a cd-rom drive in it.  The live cd loads just fine, and I'm able to complete the install fine.  But when I reboot and try to log into Ubuntu, I get this:

ata1: port failed to respond (30 secs, Status 0x80)
ata1: COMRESET failed (device not ready)


and it just repeats those two things a bunch of times and never progresses beyond that.  

I've tried reflashing my cd-rom drive, no help. Unplugging the cd-rom drive, no help.

Anyone have any ideas?

HI if you were to boot to the live cd again can you view the ubuntu partition and you may not have install the grub and you can you this thread to help you locate that and insure that is was installed. 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) 
I hope this helps in some way good luck!
Edit: post** number 1 **sounds like a good idea!

---

### Post by drocko on 2007-07-22
Chin Strap and anyone else on an x61 tablet...

Check out [this post]("http://ubuntuforums.org/showpost.php?p=3063550&postcount=16") for info about getting the tablet portion up and running. 

Good luck!

---

