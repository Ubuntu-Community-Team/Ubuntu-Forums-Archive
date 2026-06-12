---
title: "issues with the driver of a Motion Eye webcam on a Sony Vaio"
date: 2008-10-10
forum: Hardware
---

### Post by m10 on 2008-10-10
i have got a Sony Vaio VGN-FZ31S with a motion eye webcam wich does not work.

I have tried (some time ago) to install the r5u870 drivers (v. 0.11.2) and it did work once but after reboot it didn't work anymore.
I tried to fiddle around with it but nothing..

Today i wanted to give it another try and searched a bit on the net. I found this thread:
[http://ubuntuforums.org/showthread.php?t=289836](http://ubuntuforums.org/showthread.php?t=289836)
and i followed the instructions on the last post [http://ubuntuforums.org/showthread.php?t=289836&page=22](http://ubuntuforums.org/showthread.php?t=289836&page=22) (wich installs v 0.11.1 though)
but it did not work (opening cheese i see only rubbish instead of myself).

help would be much appreciated!
 
here is some info that might be useful:
```
mio@mw:~$ lsusb | grep Ricoh 
Bus 003 Device 002: ID 05ca:183b Ricoh Co., Ltd 
mio@mw:~$ uname -a
Linux mw 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux
```
PS i'm on Ubuntu 8.04 HH

---

### Post by josepcoves on 2009-01-20
Hi,

I solved that problem upgrading to  2.6.24-23-server kernel.

---

