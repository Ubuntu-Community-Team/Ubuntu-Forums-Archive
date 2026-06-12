---
title: "epson scanner v500 help deprecated driver dependencies"
date: 2024-08-31
forum: Hardware
---

### Post by snowcrash1 on 2024-08-31
so, I followed everything in tuturials an snuuff...

and now I have permission to detect my scanner, i kid you not.  It was a hassle, while now my software can detect using Sane, I can't send it commands. 
Help?  I need drivers for it but the dependencies are deprecated than what 24.04 uses a new library somewhere... libsane1.011-3 is what my dependents want, and ubuntu depends on libsane-1.211 or something.  Any help would be appreciated getting this to work.

Oh by the way, My iMac 8,1 works PRETTY WELL with ubuntu 24.04 LTS except for Suspend.  I just couldn't bear to throw away a perfectly useful computer after you know who made it obsolete.  It's dumb.

*snowcrash

---

### Post by snowcrash1 on 2024-08-31
$ scanimage > image.pnm
Output format is not set, using pnm as a default.
scanimage: rounded value of br-x from -32768 to -32768
scanimage: rounded value of br-y from -32768 to -32768
scanimage: sane_start: Invalid argument
$

---

### Post by snowcrash1 on 2024-09-05
[bump]
um, I found this useful because my fans didn't turn on this computer iMac 8.1
[https://ubuntuforums.org/showthread.php?t=2156916&page=3](https://ubuntuforums.org/showthread.php?t=2156916&page=3) [solved problem]  How to turn some fans on :)  thanks Ubuntu

---

### Post by snowcrash1 on 2024-09-06
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1707352](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/1707352)

---

