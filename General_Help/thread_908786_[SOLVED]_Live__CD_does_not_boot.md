---
title: "[SOLVED] Live  CD does not boot"
date: 2008-09-02
forum: General Help
---

### Post by Coco999 on 2008-09-02
I'm trying to work with a brand new CD (ubuntu - 8.04.1 - desktop i386, just downloaded). 

I get an error message:


[ 252.664924 ] Buffer I/O error on device sr1, logical block 32 
[ 252.668198 ] Buffer I/O error on device sr1, logical block 33
[ 259.805161 ] Buffer I/O error on device sr1, logical block 32 
BusyBox v1.1.3(Debian 1:1.1.3 - Subuntu12 Built-in shell (ash) 
Enter 'help' for a list of built-in commands
(initramfs)


If I enter 'help' I get a list of commands, most of which don't seem to work at all. One of the commans is wget, and it seems to work, so some kind of operating system seems to be loaded already, although useless to me.

However, I can boot OK with 2006 Kubuntu or Gnomix 2.10 live CDs. Also I can boot OK with the Ubuntu as quoted in another computer.

What is the trouble and what can I do?

Thank you for your help and regards.

---

### Post by monkeyking on 2008-09-02
Maybe it's a bad burn,
have you tried in on another computer

---

### Post by oilchangeguy on 2008-09-02
> **monkeyking said:**
> Maybe it's a bad burn,
have you tried in on another computer

the user already states the cd works fine in another computer.

---

### Post by oilchangeguy on 2008-09-02
> **Coco999 said:**
> I'm trying to work with a brand new CD (ubuntu - 8.04.1 - desktop i386, just downloaded). 

I get an error message:

[ 235.029652 ] Buffer I/O error on device srl, logical block 32 memtest 86+ 201

However, I can boot OK with 2006 Kubuntu or Gnomix live CDs. Also I can boot OK with the Ubuntu as quoted in another computer.

What is the trouble and what can I do?

Thank you for your help and regards.

please provide the specs for your computer.

---

### Post by Coco999 on 2008-09-02
> **oilchangeguy said:**
> please provide the specs for your computer.

The computer is a Pentium IV with 1 GB RAM and I think it runs at 1600 MHz.a

---

### Post by Coco999 on 2008-09-05
I marked this thread as solved because I tested with yet another version, 7.04, and it booted OK, confirming that there is a bug in the new 8.04, that makes it incompatible with certain hardware configurations. I hope the development team are aware of this and will correct this for 8.10. 

Many thanks to all who replied.
Regards.

---

