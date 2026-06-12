---
title: "How do I check the cause of a system freeze?"
date: 2008-11-05
forum: General Help
---

### Post by mjpatey on 2008-11-05
Hi, all-

I've been having a problem which I believe can be isolated to a hardware issue.  From time to time, my system just freezes and cannot be recovered except by powering down and rebooting.

When the freeze happens, the "Caps Lock" and "Scroll Lock" indicator lights on my keyboard flash in unison at about 1x/second, indefinitely, until I power down.

When I reboot, I want to check a log file or something, but don't know where to begin.  Any ideas?

Thanks for your help!

-Mark

---

### Post by Coreigh on 2008-11-05
I am sure someone will offer more detailed answers but you can start here.

System >> Administration >> System Log

---

### Post by TwiceOver on 2008-11-05
Not sure what your setup is, but I believe on Dell laptops this indicates a memory issue.  I have seen this happen in the past and a memtest confirmed bad memory.

Next time you restart enter the Grub menu and do the memtest check.

---

### Post by fancypiper on 2008-11-05
I would check these files:

/var/log/messages
/var/log/syslog

---

### Post by mjpatey on 2008-11-06
I ran Memtest86+ for about 5 hours or so, and it completed more than 6 passes.  The results are in the first attachment.  It does show some errors in the red section.  So are these likely what's causing my system to lock up?  I don't have a feel for how many memory errors would be enough to cause trouble.

Also, when I reboot, I occasionally get the message in the second attachment:

```
Boot from (hd1,0) ext3  [then a bunch of numbers]
Starting up...


crc error

 -- System halted_
```CRC is a checksum, right?  So something's physically wrong with one of my hard drives, as well, maybe?

Thanks for any light you can shed!

-Mark

---

### Post by cicatrix1 on 2008-11-06
memtest shouldn't show any errors.  That's bad.  CRC error can easily be caused by bad RAM.  Get new RAM :)  If you have multiple sticks, only one may be bad.  You'll have to figure that out by trial and error... i.e. replace one, rerun memtest.

---

### Post by kubug on 2008-11-06
Yes, like cicatrix1 said, your memory is bad. 

Unless you have done some overclocking, the memory went bad on you. What are your hardware specs? Laptop or Desktop? Did you build it?

---

### Post by emadwilliam on 2008-11-06
System freeze may happens due to error in the RAM, check your memory status using the memtest provided with the Ubuntu CD.

---

### Post by mjpatey on 2008-11-06
Thanks, everyone.  I'll remove my RAM a stick at a time and see how it goes!

-Mark

---

### Post by mjpatey on 2008-11-06
By the way, it is a home-brew desktop.  :-)

---

### Post by kubug on 2008-11-07
> **mjpatey said:**
> By the way, it is a home-brew desktop.  :-)

If it is a homebrew, you may have a BIOS setting wrong. Especially with the newer DDR2/DDR3 you have to double-check the voltage setting for the memory in the BIOS. 

I know, since my computer is a homebrew as well. In my case the BIOS only set a 1.9V to my DDR2, eventhough it needed 2.1V. 

So it may not be bad hardware, but rather a bad BIOS setting.

---

