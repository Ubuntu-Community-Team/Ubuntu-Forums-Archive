---
title: "scanning with xsane from canoscan lide 60"
date: 2017-11-21
forum: Hardware
---

### Post by jimjo on 2017-11-21
I have an canoscan lide 60 connected 2 an mint 18.2 operating system.
I installed xsane, xsanae-commons, xsane-doc and libsane.

The scanner is detected by xsane but when it is trying to scan it results in "Failed to start scanner: Document feeder jammed".
There is an dead link to an mini how2 on this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon)
With the information there i could handle it myself, but without i hope you can help me.
I have the same problems like Alan F in this thread [ [https://ubuntuforums.org/showthread.php?t=899605]](https://ubuntuforums.org/showthread.php?t=899605]) except that my cable is working and tested.
 Alan F stated that he did 3 things that helped him following the mini how2:
1. "sane-find-scanner command was OK"
   >>>i guess he means Xsane is detecting the scanner. That works !!
2. "dll.conf modified as shown" 
3. "45-libsane.rules did not exist but I created it and added the lines as shown"

If you could figure out what step 2 and 3 include, or could provide other solutions you would be very helpful.

With regards, Johann

[We are providing a school in the Netherlands (free, natural learning based on selfdetermination and basicdemocratic values) with debian-kde-edu terminals including a lot of tweaks. The scanner will be placed in the kids office]

---

