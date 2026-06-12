---
title: "ALC275 Issues with internal and external Microphone"
date: 2010-05-02
forum: Hardware
---

### Post by intelligentforu on 2010-05-02
Hello Ubuntu Development Team,

I first want to say I LOVE Ubuntu and where it has come.

Secondly, I want to thank all the developers in all the sub system teams.

I have tried without success to make my RealTek ALC275 work correctly with the internal microphone.

It requires a special patch to the realtek sources and a compile of the kernel. I do not want to void any support. 
 
It appears this BUG is slipping through the cracks and I need to know when the RealTek ALC275 is going to be supported? The current implementation of using ALC269 is not working for the ADC's and pin selections.

The PPA Audio Team seems to not have this bug reported properly.

What can we do to get this RealTek ALC275 supported properly in and LTS release?

Needing it like 2 months ago!

Cheers,
Noel

---

### Post by luopio on 2010-08-09
according to [http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone](http://code.google.com/p/vaio-f11-linux/wiki/EnableMicrophone)

the darn patch should be included in 2.6.36. i guess there are now ppa's with patched files?

---

