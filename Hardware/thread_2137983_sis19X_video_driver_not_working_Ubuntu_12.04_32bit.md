---
title: "sis19X video driver not working Ubuntu 12.04 32bit Desktop"
date: 2013-04-22
forum: Hardware
---

### Post by SteffJay on 2013-04-22
Hello all. I have installed the above distro. However, when booting, all i have is a flashing screen !!!

First question: How do i stop from booting into the desktop environment to get the command line?

Second: What syntax do i use to drop the resolution to a lower one?

Third: If that is not possible; can i SSL into the OS from another pc to correct the problem as root?

Thanks in advance.

---

### Post by deadflowr on 2013-04-22
If I was given the choice between using a hammer to my skull and dealing with SiS graphics drivers, I'd rather punch a hole in my skull.
But anyway, if there is any solution for you it would be here
[http://www.winischhofer.net/linuxsispart1.shtml](http://www.winischhofer.net/linuxsispart1.shtml)

---

### Post by mörgæs on 2013-04-22
Eh - I thought SIS190 and SIS191 (assuming you are talking about them) were network cards...?

Please run **sudo lshw > lshw.txt** and post lshw.txt in CODE tags. If you can't access the command line it can also be done in a live boot.

---

### Post by sanderj on 2013-04-22
> **deadflowr said:**
> If I was given the choice between using a hammer to my skull and dealing with SiS graphics drivers, I'd rather punch a hole in my skull.


LOL! And .. I second that: I once bought a laptop with a SiS 761 / 762 VGA chipset. Big, big mistake. SiS did not release open source drivers, nor specs for programmers, not binary drivers for the Linux version I had.

Since then I only buy hardware with video hardware with open source drivers ... meaning I only buy laptops with Intel GPU.

---

### Post by mörgæs on 2013-04-22
Let's put the complaints about SIS to rest, get back on track and wait for Steffjay to respond.

---

### Post by SteffJay on 2013-04-22
Thanks for the quick reply's guy's. Oh dear........... My bad. I'm working on two systems here and I'm afraid one grey cell has overwritten the other :( I will start a new thread.

---

