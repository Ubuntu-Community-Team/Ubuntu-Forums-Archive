---
title: "Ubuntu 10.04 Lucid Lynx fails to start in Gateway 4530GZ"
date: 2010-05-12
forum: Hardware
---

### Post by Virus666 on 2010-05-12
Hi all,

As it says in the title Ubuntu 10.04 Lucid Lynx does not start in **Gateway  4530GZ** notebook. It is the final release of Lucid and I can confirm  that is not a Grub boot issue. While the "x" is starting video  crashes and Lucid fails to start.

Here are some hardware information:

**Processor:**  Intel Pentium  M 725 (1.6 GHz)
**System Memory:** 2 GB 333 MHz DDR RAM
**Chipset Type:**  Intel 855GM
**Video:** Intel with 32 MB UMA Video Memory (chipset integrated)
**Audio:** PC2001 compliant AC' 97 audio

Full info:
[http://support.gateway.com/s/Mobile/Gateway/4536GZ/4095sp3.shtml](http://support.gateway.com/s/Mobile/Gateway/4536GZ/4095sp3.shtml)
[http://reviews.cnet.com/laptops/gateway-4530gz/1707-3121_7-31200464.html?tag=mncol;lst](http://reviews.cnet.com/laptops/gateway-4530gz/1707-3121_7-31200464.html?tag=mncol;lst)

I have tried both x86 and x64 desktop and alternate install cds with no success. The  performance of Lucid appreciable but it would be nice to try it in my own notebook...

Thank you... :-)

---

### Post by ronnielsen1 on 2010-05-12
> 
I have tried both x86 and x64 desktop and alternate install cds with no success.
Well, the 64 is definitely not going to work. 

What kind of errors does it give you?

---

### Post by Virus666 on 2010-05-12
Well,

Actually it is a shared PC and my fried experienced the problem which I mentioned before. Since I do not have the PC with me at the moment I can say just "the video crashes while the x was trying to start." However, I found an issue in Ubuntu Wiki about the X and Intel chipsets.

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Gateway 4530GZ's chipset is Intel 855GM and according to wiki Lucid's X has several unsolved problems with "i845, i855 and other 8xx chips"... So, is  Intel 855GM one of those chipsets? If so, I'll try to find a workaround according to that document. I'll you inform the forum about the situation.

Thank you...

---

### Post by ronnielsen1 on 2010-05-12
Good Luck. I have an older Intel 82845G built in that will work but makes me jump through hoops. I have a newer Nvidia I'd like to throw in it but it's got a worthless BIOS and I can't figure out how to turn onboard video off.

---

### Post by Virus666 on 2010-06-06
Solved!

The first solution related to  i845, i855 and other 8xx chips in Ubuntu wiki worked for Gateway 4530GZ. My friend confirmed that "Workaround A: Re-enable KMS" worked.

Thank you... :-)

---

