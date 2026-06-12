---
title: "sound card help"
date: 2004-12-30
forum: Hardware &amp; Laptops
---

### Post by cacofonix on 2004-12-30
I need help getting my realtec audio card to work. I know how to do it I just need to get the components needed. 

I need to get the kernel-headers which Isnt the problem the problem is it doesnt have my kernel image headers I get these instead:
```

$>sudo apt-get install kernel-headers
Reading Package Lists... Done
Building Dependency Tree... Done
Package kernel-headers is a virtual package provided by:
  kernel-headers-2.6.7-1-k7-smp 2.6.7-1ubuntu2
  kernel-headers-2.6.7-1-k7 2.6.7-1ubuntu2
  kernel-headers-2.6.7-1-686-smp 2.6.7-1ubuntu2
  kernel-headers-2.6.7-1-686 2.6.7-1ubuntu2
  kernel-headers-2.6.7-1-386 2.6.7-1ubuntu2
  kernel-headers-2.6.7-1 2.6.7-1ubuntu2
  kernel-headers-2.4.26-speakup 2.4.26-1
  kernel-headers-2.4.26-1-k7-smp 2.4.26-6
  kernel-headers-2.4.26-1-k7 2.4.26-6
  kernel-headers-2.4.26-1-k6 2.4.26-6
  kernel-headers-2.4.26-1-686-smp 2.4.26-6
  kernel-headers-2.4.26-1-686 2.4.26-6
  kernel-headers-2.4.26-1-586tsc 2.4.26-6
  kernel-headers-2.4.26-1-386 2.4.26-6
  kernel-headers-2.4.26-1 2.4.26-6
You should explicitly select one to install.
E: Package kernel-headers has no installation candidate
$>uname -r
2.6.8.1-4-686-smp

```
why cant I get the headers for my kernel when I got it from apt in the first place? lol

secondly I might have to rebuild the kernel and I need to get ncurses-devel to do it what is it called so I can apt it?

cheers 

cacofonix

---

### Post by WiLLiE on 2004-12-30
Build Tools + Kernel Headers:

sudo apt-get install build-essential linux-headers-`uname -r`

---

### Post by cacofonix on 2004-12-30
I was putting in the wrong command for the headers Thanks for the help WiLLiE

---

