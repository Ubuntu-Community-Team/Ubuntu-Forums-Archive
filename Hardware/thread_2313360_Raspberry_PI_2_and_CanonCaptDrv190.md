---
title: "Raspberry PI 2 and CanonCaptDrv190"
date: 2016-02-11
forum: Hardware
---

### Post by HANZ99 on 2016-02-11
I'm trying to run a Canon LBP6000.  I want to print from my PI to A Win 7 having a Canon LBP6000  attach to a USB port.  I can connect via a network system (Sharing LBP6000), but I cannot get CUP on my PI to run.  Can I use then CanonCaptDrv190 pdd for my LBP6000? How do I download it from the CanonCaptDrv190??   I've read the info, but I  do not know must about Ubuntu.  (I'm a Win 7 person).


Can You help??


Thanx in advance...


Hanz


[h=1][/h]

---

### Post by Vladlenin5000 on 2016-02-11
Direct or networked, all printers require drivers which can already exist in your distro or need to be installed. It's no different than other OSs.

---

### Post by HANZ99 on 2016-02-11
How do I download the info on the LBP6000.   What commands do I need to use??   I appreciate any the help you can give me..  Thanx

---

### Post by Vladlenin5000 on 2016-02-11
It may or may not depend on what OS you're actually running in the Pi, you forgot to mention it...
Assuming it's Ubuntu or Ubuntu based then: [http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04/464334#464334](http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04/464334#464334)
Something that you can easily find by googling, BTW.

---

### Post by HANZ99 on 2016-02-11
The files (wget [http://gdlp01.c-wss.com/gds/6/0100004596](http://gdlp01.c-wss.com/gds/6/0100004596))) are not there.  Look like the web site delete them.  

The OS [h=3]Raspbian Jessie[/h]             Full desktop image based on Debian Jessie

Hanz

---

### Post by coldraven on 2016-02-12
> **Vladlenin5000 said:**
> It may or may not depend on what OS you're actually running in the Pi, you forgot to mention it...
Assuming it's Ubuntu or Ubuntu based then: [http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04/464334#464334](http://askubuntu.com/questions/463289/cant-get-my-canon-lbp-printer-to-run-under-ubuntu-14-04/464334#464334)
Something that you can easily find by googling, BTW.

The binary file mentioned in that link is compiled for i386 and not ARM. I presume that it will not run in Raspian. It's also closed source so it is not possible to compile it yourself.

---

### Post by Vladlenin5000 on 2016-02-12
Oooops, my bad. You're right. And I'm afraid it probably won't work in armhf.
That's the problem about proprietary drivers.

---

