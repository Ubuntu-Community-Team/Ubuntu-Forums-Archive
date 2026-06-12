---
title: "lenovo g575 64 bit or 32 bit?"
date: 2013-01-16
forum: Hardware
---

### Post by ilikekitties on 2013-01-16
Hi all,

I have a lenovo g575. I'm thinking abouting putting xubuntu on it for faster performance. I admit I'm pretty ignorant about specs, is the dual core 64 bit or 32. here is the cpu info. Just wondering if I want the 32 or 64 bit image of xubuntu


@:~$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 20
model        : 2
model name    : AMD E-450 APU with Radeon(tm) HD Graphics
stepping    : 0
microcode    : 0x5000101
cpu MHz        : 1650.000
cache size    : 512 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 2

---

### Post by tgalati4 on 2013-01-16
Most newer CPU's support 64-bit.  You will get an error message "Wrong Architecture" if you try to run or install 64-bit on a 32-bit processor.  64-bit will use more RAM, because of the larger address space.  So if you have lots of RAM go with 64-bit.  If you are low on RAM, and can't or don't want to add more RAM, then go with 32-bit.

---

