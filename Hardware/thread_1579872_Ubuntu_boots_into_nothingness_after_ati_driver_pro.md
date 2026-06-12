---
title: "Ubuntu boots into nothingness after ati driver problems"
date: 2010-09-22
forum: Hardware
---

### Post by messie on 2010-09-22
Greetings,


I have a great great problem. My ubuntu 10.04 installation seems at steak, as I cannot boot into ubuntu. It seems like I have messed my drivers of ati. I own a 4650HD radeon. After a lot of searching , I managed to install the xorg drivers and stuff, And all went well until I performed an update which totally messed everything up. After that, I had no graphx acceleration and on top of that a package of fglrx (or sth) kept crashing after each update. Now after fiddling around with the package, ubuntu boots into a black screen. I have tried ctrl-alt-F1, but no go.... Any help will be much appreciated.

---

### Post by Tylerjd on 2010-09-22
I have heard (and experienced) problems with NVIDIA cards not being great with ubuntu... But not ATI... This might help, after a quick google search: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


You may need to uninstall manually the packages that you installed before the problems by using the rescue mode in the manuel options when you boot from a cd, in Ubuntu before 10.04, it was in the default CD menu, but with Ubuntu 10.04, you need to hit an f-button (like f5) while the CD is starting (at the purple screen, with the ubuntu logo at the bottom, and no loading dots).

Hope this helps!

---

### Post by messie on 2010-09-22
Thanks a lot for your help.


I have managed to boot to a terminal using recovery mode but I have no idea what to do next... The link does not help much either, it mentions the drivers for ubuntu 9.10 while i am on 10.04....

edit:I tried to do these
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)
and now i ended up with ubuntu loading but freezing at the ubuntu logo with the orange dots....

---

