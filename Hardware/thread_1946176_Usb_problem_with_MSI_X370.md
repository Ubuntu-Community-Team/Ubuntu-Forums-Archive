---
title: "Usb problem with MSI X370"
date: 2012-03-24
forum: Hardware
---

### Post by dumaron on 2012-03-24
Hi to all,
I'm having a problem with Ubuntu and usb on a MSI X370 netbook.
With Ubuntu 11.10 every usb device won't work and dmesg said there are logical error.
So i tried Fedora 16 and Windows 7, but with these OS there wasn't problem.
Thinking that it might be a kernel problem (ubuntu has kernel 3.0 and fedora 3.1) i tried to update to ubuntu 12.04 (kernel 3.2), but the problem persists.

Any idea?:confused:
Excuse me for my english!

---

### Post by iyas120 on 2012-04-26
Yes i am experiencing the same problem.. it is a bug with AMD E-350 motherboard?

---

### Post by iyas120 on 2012-04-26
found this temporary solution

the only solution is to blacklist rts5139:

sudo gedit /etc/modprobe.d/blacklist.conf

blacklist rts5139

from : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863152?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863152?comments=all)

edit: today i am installing ubuntu 12.04 and the bugs is still there.. this is the only solution

---

### Post by dumaron on 2012-04-28
I've waited to see the 12.04 release, but the problem still persists.
Your solution worked for me, thank you so much.

---

### Post by algebralives on 2012-04-28
Thanks so much for the solution, iyas120. Works perfectly.

---

### Post by iyas120 on 2013-01-11
With new kernel on ubuntu 12.04.1 and above.. this problem is solved by default. Thanks to kernel team...

---

