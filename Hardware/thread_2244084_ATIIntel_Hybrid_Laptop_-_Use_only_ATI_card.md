---
title: "ATI/Intel Hybrid Laptop - Use only ATI card"
date: 2014-09-13
forum: Hardware
---

### Post by joe15 on 2014-09-13
Hello everyone, I am running Ubuntu 14.04 and I have an ATI Radeon Mobility 5650 as well as an Intel HD 2000 in my Hp dv6t3000 laptop. I am using the opensource drivers currently, xserver-xorg-video-ati. What I would like to do is use the ATI 5650 card instead of the Intel HD 2000 but I can't seem to figure out how. I took a look at the Hybrid graphics section on the arch wiki, as even though I am on ubuntu it is still well documented, and it says that there is something called DPM which will let me enable/disable certain graphics on kernels 3.12 above. ubuntu 14.04 uses kernel 3.13 so I should have this feature right? I can't seem to find it though. Any help?


Thank you
Regards,

---

### Post by grahammechanical on 2014-09-13
These may help you

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

[https://github.com/beidl/amd-indicator](https://github.com/beidl/amd-indicator)

Regards.

---

### Post by joe15 on 2014-09-14
So I just install fglrx and it should work? In the past this would cause me to not have X boot up and only have a terminal...however I do not remember if this was with 13.10 or 14.04. I am afriad to try it honestly. Is there anyway you can confirm I will be fine?

---

### Post by joe15 on 2014-09-21
I installed amd-indictor .deb package from github. It seemed to also have installed fglrx. Upon reboot X failed to start and I had to remove and purge fglrx and install the open source drivers. What other option is there for me?

---

### Post by SeijiSensei on 2014-09-22
I use only the AMD adapter on an HP machine by making a change to the BIOS settings.  In my case, I needed to set the adapter to "fixed mode."  After that, fglrx works as expected.

---

