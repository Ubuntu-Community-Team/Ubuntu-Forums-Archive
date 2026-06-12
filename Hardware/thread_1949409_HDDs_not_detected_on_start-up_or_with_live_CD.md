---
title: "HDDs not detected on start-up or with live CD"
date: 2012-03-30
forum: Hardware
---

### Post by mashedbear on 2012-03-30
My system has 2 hard drives and OS is Ubuntu 11.10 64bit. No other OS installed. both hard drives are EXT3 file system

As of this morning the machine won't start up in to ubuntu and I get a bios (I think) error on start up: no ide hdd master detected press f1 to continue. 

Using a live CD I can get Ubuntu operating (using the  1st option to try ubuntu without changing the system). However once ubuntu has loaded I can not see either of the two internal hard drives. I can see an external hard drive (connected via USB). 

Would like to use the live CD to repair the fault (with grub?) and get my system back. 

Help and advice appreciated!

---

### Post by Bill Z on 2012-03-30
Without being there, it sounds like a hardware problem.  A controller problem. 

Try this:  With the power on the computer set to off, remove one of the hard drives, then restart your machine.  If you get the same error, try putting that drive back in the computer and removing the other.  If nether work, then chances are that is is the controller.  Just to make sure and if you have another good drive somewhere, use just the known good drive and try booting.  I'm betting it won't be recognized ether.

Try the above and let us know what happens.

---

### Post by mashedbear on 2012-04-02
Thanks - did exactly as you suggested. One of the hard drives has failed. Curious that the 'good' hard drive was not detected with live CD running, until the bad drive was removed.

Oh well, bought new SSD (so something hopefully good will come of the aggravation) and will install as soon as it arrives. 

Interesting though, the live CD I had was Ubuntu 9.10 & the old or should I say classic Gnome was like a long lost friend. Now booting of an 11.10 live CD and well its just not as good....  shame really. 

Thanks for your advice about the hdds.

cheers

---

