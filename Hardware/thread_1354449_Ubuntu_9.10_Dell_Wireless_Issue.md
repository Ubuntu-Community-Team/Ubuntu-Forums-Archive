---
title: "Ubuntu 9.10 Dell Wireless Issue"
date: 2009-12-13
forum: Hardware
---

### Post by DBruce on 2009-12-13
I just installed Ubuntu 9.10 on my Dell Inspiron 1525 and hav been unsuccessful in getting my wifi working.

I am a NOVICE user with my only experience being "proprietary" Unix to manipulate hardware, in a very limited and controlled environment. 

What I am hoping for is something along the lines of "for Idiots" explanation of what I need to do to get this working, a "cheat sheet" if you will.

So far I love the OS but wifi is a , "gotta have it" deal breaker for me. 

Thanks

DBruce

---

### Post by DBruce on 2009-12-14
After much searching it appears I need to give the community a little more info about my system to get help on the issue I have.

Wireless card is listed as: "Dell wireless 1395"

The chipset is listed as: "BCM 4315/BCM22062000

If anyone has the directions to get the above wireless card going, please let me know.

I have found several things that are supposed to fix this but I lack the understanding of the language to get this to happen.

Additionally, if I have to, I can connect to a cable with ubuntu running if it makes this easier.

Thanks

---

### Post by ianmillington on 2009-12-14
I can't profess to know a great deal about this card - the one in my Dell works OOTB- but from what I have read you need to check whether any proprietary drivers are available - check in hardware drivers under system which should tell you whether there is any hardware needing proprietary drivers. Otherwise (assuming you have a wired connection!) :



1. You can install a package called ndiswrapper, which will enable you to use the windows .inf files for your hardware - that is usually viewed as the last resort

2. You may find that the package b43-fwcutter works with this card. It is available in the package manager. Once installed reboot.

Hope this helps. Let us know.

Ian

---

