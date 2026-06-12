---
title: "pocket pc that runs linux so i can sync with a linux desktop"
date: 2008-05-16
forum: Hardware
---

### Post by keiffee30 on 2008-05-16
i know of this may have been asked before and there are loads of posts in many forums but i have just about given up on windows (well 99%).

The only device i have left is a HP ipaq h1930 (asamsung s3c2410). Is there a way of getting linux on to this device so i can sync this with Evolution 2 without any problems.

........OR .............

Is there a pocket PC that runs linux already that i can buy that will do the job.

Im looking for a...
calendar
tasks
note pad
address book.

so what way do i keep going. at the moment i have running Ubuntu 7.10 and Virtual box with Win XP just for my Ipaq to sync with outlook (no emails).


Any comments would be lovly

---

### Post by Sef on 2008-05-16
Read [this]("http://osdir.com/ml/handhelds.ipaq.synce.general/2007-10/msg00036.html").

---

### Post by keiffee30 on 2008-05-16
thanks Sef i have looked at the link you have given me and i have started to install 

Kernel driver i have download the following tarball:  

**usb-rndis-lite-0.11.tar.gz** 

* Extract and install the driver in the following way:

[B]$ make
$ sudo ./clean.sh
$ sudo make install[/B]

This all went ok. Now when i got to the core libraries, i have typed in 

**sudo apt-get install odccm librra-tools librapi2-tools**

and this is what i got 

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package odccm[/B]

---

