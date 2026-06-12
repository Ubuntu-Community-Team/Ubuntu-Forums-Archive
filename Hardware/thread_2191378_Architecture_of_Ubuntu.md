---
title: "Architecture of Ubuntu"
date: 2013-12-02
forum: Hardware
---

### Post by joblacker on 2013-12-02
I'm not an operating system expert, but I have used and understand MS Win fairly well.  What I need to understand is more about the Ubuntu (and linux in general) hardware environment better so I can further understand why it's so difficult and cumbersome to get a DVB-T dongle to work in Ubuntu.  When I boot Ubuntu, then do a lsmod, I can see that a module has been loaded which appears to be the "driver" for the rtl28xxu dongle.  I would expect that when and if I load an application like HDSDR, it would be able to "talk" to that device via the loaded kernel driver.  Yet, what I'm finding is that's not the case.  

Searching across the internet, I find references to software that in some way enters the equation:  BorIP, rtl (and it's various utilities, zadig, gr_baz, etc.).  Now I do understand that HDSDR runs under Wine, so that may have something to do with what's going on, but I really don't know for sure.

I also would have thought that the dongle being a usb device, I would be able to fire up virtualbox and then run HDSDR under win7 in the "box" but, unfortunately, the "in-the-box" win7 doesn't see the DVB-T dongle at all.

So, can someone help me understand the environment sufficiently so I can make some educated searches to find the software I need to make this DVB-T dongle work with, for example, HDSDR?  

As an aside, I've been able to get the dongle to work with a program named SDRSharp under mono, by using the rtl_tcp "utility" after first temporarily disabling the rtl28xxu kernel module.

Thanks in advance for any help.

---

### Post by sanderj on 2013-12-02
Rule 0: Linux is not Windows
Rule 1: so try to avoid to run hardware-oriented Windows software on Linux
Rule 2: use native Ubuntu tools

Are you willing and able to do that?

---

