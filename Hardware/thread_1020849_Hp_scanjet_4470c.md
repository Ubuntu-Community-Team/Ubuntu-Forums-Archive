---
title: "Hp scanjet 4470c"
date: 2008-12-24
forum: Hardware
---

### Post by RobFS1 on 2008-12-24
I recently obtained a Hp scanjet 4470c from a thrift store. It was recognized by my windows machine, but I tried it in my ubuntu computer with no such luck. I read on the internet that you could open a terminal or synaptic and get backends for sane, which I installed and found that the scanner did work after some tinkering. The problem is that it doesn't scan in color. My question is: can the printer work on ubuntu and scan in color?

---

### Post by RobFS1 on 2009-05-28
It has been almost 6 months now, and still, no answer. :( Please will someone answer.

---

### Post by mugedoc on 2009-06-02
sudo apt-get install libsane-extras

[https://sourceforge.net/project/showfiles.php?group_id=121985](https://sourceforge.net/project/showfiles.php?group_id=121985)

This scanner is based on a RealTek RTS8891 chip of wich there aren't specs. It's not supported by sane, there's only an unofficial driver at [http://reapoff.sourceforge.net/hpscanner/Default.htm\](http://reapoff.sourceforge.net/hpscanner/Default.htm\) but it doesn't still works well.

This information I'm found in 
[http://www.linuxcompatible.org/HP_ScanJet_4470c_c9938.html]("http://www.linuxcompatible.org/HP_ScanJet_4470c_c9938.html")

I hope that you have helped

---

### Post by gerolami on 2009-11-04
Ok,

I managed to get this scanner to work with the last release of Ubuntu.  However, when I upgraded to 9.2, the scanner stopped working.  I still have the same additional back-end installed, but now it does not work.  Does anyone have any ideas what changed?

---

### Post by anotherone33 on 2010-06-05
hi guys,
xsane / sane / compatibility problems solved !

I've just connected my scanjet hp scanjet 4470c - ubuntu lucid lynx 10.04 x64 and it works with Xsane !  All resolutions, till 1200.


Just now I had problems with 9.10 (x86) (see the scanner but not works), tried your solutions/patch/tries but it will not works and now I'm upgrading on that pc station. I looked at your problems. Maybe also you have solved ! But I've not found any good answer searching for it, so, this one.

bye.

---

