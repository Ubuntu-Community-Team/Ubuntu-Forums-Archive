---
title: "Trouble booting up with ubuntu 10.10"
date: 2010-10-17
forum: Hardware
---

### Post by brndndvr on 2010-10-17
Hey all!
I just bought an older Dell Inspiron 8300 and plopped a 1 TB Western Digital Hard drive in it. The BIOS is A05 and I believe it's from Phoenix.  Also, the clock battery was dead, so I replaced that with a  new one.  The main purpose i bought it was in hopes of trying out ubuntu for the first time, but I've been having all sorts of troubles. 

What happens when I turn on the computer?
1. Turns on and almost instantly beeps twice and gives me this message: Press F1 to retry, F2 for setup options.
2. Regardless of what I tell the system to boot up with, I get this message.  
3. If I put the IDE CD drive at the top of the list with the disc in it, it will spin up for about 10 seconds, and then the same dreaded message will show up. 

What hasn't worked:
1. I have tried setting the boot order to make the computer boot off the CD drive with no luck (with a working .iso copy of ubuntu on it) - I can boot up ubuntu with this disc on my laptop, but the dimension desktop has had no such luck.
2. I have tried booting off a USB that has ubuntu on it as well.
3. I've double and triple checked the connections inside the tower and everything seems to be in order.  
     - Everything is detected: Primary SATA drive is the drive I just installed, and the two DVD drives are both detected as primary master and primary slave drives.

Does anybody have any ideas?  I am a noob so I'm about out of ideas.  The last thing I'm going to try before breaking out the hammer (unless someone intervenes) is using a different install disc...perhaps the fairly old dvd drives don't like the black CD that I put ubuntu on.

---

### Post by brndndvr on 2010-10-17
Anybody??

---

### Post by brndndvr on 2010-10-17
Problem solved, my slave drive was the only good drive, switching that with the master fixed the problem.

---

