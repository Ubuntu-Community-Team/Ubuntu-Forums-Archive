---
title: "i386 Lucid Quirks w/4GB RAM"
date: 2010-06-08
forum: Hardware
---

### Post by schmickey on 2010-06-08
I have installed 10.04 several times on my laptop and I get inconsistent reports from System Monitor about how much RAM I have (4 GB).  I'm installing 32-bit Lucid only.  On some installs System Monitor reports 2.9 GB but after other installs it will report 3.8 GB.  Now, I would expect it to report the 3.8 if I were using the AMD64 edition -- but, I'm not.

I've done about a half dozen installs followed immediately by updates.  Perhaps the problem is fixed now since the last 2 installs reported the 2.9.

I seem to remember reading somewhere that Linux will use all 4 GB of ram even when using the 32-bit version.  If so, why does it only report 2.9 GB?

I know about Window's limitations (32-bit) regarding more than 3 GB of RAM, but I was under the impression that Linux did not have those limitations.

Any explanation would be very much appreciated.

Thanks.

---

### Post by PRC09 on 2010-06-08
I think (it did for me anyway) the 32bit install of Lucid when more than 3 GB of ram is detected the PAE kernel is installed automatically....For reference see the following link.Not sure about previous versions of Ubuntu tho,but you could manually install the PAE kernel.


[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by schmickey on 2010-06-09
Thanks for the reply and explanation.  I probably would never have found that solution without your help.  I have the PAE kernel installed now and System Monitor is reporting 3.8 GB.

I may try the AMD64 version soon (I'm waiting for 64-bit Flash and Java to be available in the regular repos).

---

### Post by krippa on 2010-06-10
Flash is not available on 64-bit? I've been running 64-bit Ubuntu for about year and have always gotten it from ubuntu repos, never found a problem there, you just have to install the non-free one to get adobe version.

Java is another story.. It is supported but you must first enable partner repositories in "Software Sources", then the sun-java6-plugin will appear and install fine. What I can only assume is a bug in 64-bit Lucid, Ubuntu Software Center says "not available for 64-bit" when trying to install sun java plugin but this is obviously not true...

---

### Post by cascade9 on 2010-06-10
> **krippa said:**
> Flash is not available on 64-bit? I've been running 64-bit Ubuntu for about year and have always gotten it from ubuntu repos, never found a problem there, you just have to install the non-free one to get adobe version.

AFAIK, the repo version is 32bit flash in a wrapper. 

I find that the proper 64bit flash is less buggy, but obviously some people havent had any bugs with the 32bit version in  awrapper....

---

