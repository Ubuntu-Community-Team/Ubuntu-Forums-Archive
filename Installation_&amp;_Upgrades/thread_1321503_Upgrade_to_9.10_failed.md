---
title: "Upgrade to 9.10 failed"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by franco81 on 2009-11-10
I was running 9.04 on a Toshiba laptop satellite p200-1ee, 9.04 ws up to date, I upgraded to 9.10 via the upgrade manager. 

I got a message saying (right at the end of the process) upgrade aborted, I clicked OK, then I got a message saying upgrade complete. I clicked OK. Then the dialog which navigates a user through the process closed before the 'cleaning up' and 'restarting' parts were triggered or completed.

I restarted the computer and cannot boot into Ubuntu 9.10, gets halfway through and hangs without command prompt access. 

I've created a CD with the ISO image for Ubuntu 9.10, can I fix the upgrade this way? How can I fix this install or roll back please.

---

### Post by Ms_Angel_D on 2009-11-10
Upgrades are horrible tricky things, sometimes the work sometimes they don't. From the sounds of it, I would just use a live cd to back up your goodies and then do a fresh install.

---

### Post by franco81 on 2009-11-10
What is a live CD and where can I get one please?

Also is there a how to on backing up my files using the live CD?

I have the Ubuntu 9.10 ISO burned and tried to load from that but I got the same error and the system continues to hang at the same point:

ieee1394: Host added: ID: BUS[0-00:1023] GUID[00023f7aae40c3e0]

Thanks for the quick reply.

---

### Post by synicalx on 2009-11-10
A LiveCD is what your using - a CD with Ubuntu burned onto it. If the 9.10 CD isn't working, try a 9.04 or 8.10 CD.

To back stuff up from a live CD is easy, if it's just music, docs, photos etc you can probably just drag and drop onto an external HDD. But I would advise a more 'complete' backup, [this page]("http://ubuntuforums.org/showthread.php?t=35087") seems pretty useful

---

### Post by awam66 on 2009-11-10
> **franco81 said:**
> What is a live CD and where can I get one please?

Also is there a how to on backing up my files using the live CD?

I have the Ubuntu 9.10 ISO burned and tried to load from that but I got the same error and the system continues to hang at the same point:


The ISO you burned is the live CD. Did you do an md5check sum on the ISO file before you burned (instructions are on the Ubuntu download Web page) it and have you checked the CD for errors (on the menu when you boot from the CD) If not you may have a corrupt CD which would account for it hanging?

---

### Post by franco81 on 2009-11-10
I get that same error every time I boot up, regardless of using live CD. I have a dual boot with Vista, is there any way for me to get the files from my Ubuntu partition backed up from Vista?  Getting a bit desperate - the ISO for Ubuntu 9.04 refuses to burn onto disk.

---

### Post by franco81 on 2009-11-10
I used Explore2fs 

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

To pull the files from the ext3 partitions onto Vista, then going to try reinstall of ubuntu at a later date.

---

