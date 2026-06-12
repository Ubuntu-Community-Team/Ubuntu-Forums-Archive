---
title: "no smp"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by Fedora_Recovery on 2005-09-19
hi, yall. thanks in advance for the forums you've got here.

my problem is such:


i'm on hoary hedgehog, version number???? i downloaded it in august after i read july's inux journal featuring ubuntu, and it was the newest one. i downoaded it because FC3 was giving pretty poor performance in some areas.


i'm running tyan thunder k7 dual-proc mobo with 1 gig ecc ram, some variety of geforce4, and some cheap soundcard.

ubuntu didnt recognize the dual processors, which i was fine with because i knew apt-get could install an smp kernel for me...

problem is, it can't. am i doing something wrong?

here is my terminal:

root@Labyrinth:/home/trevor # sudo apt-get install linux-386-smp
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-386-smp

btw, i wasn't logged in as root, i was just using root terminal.

why can't it find the package? also, if possible, could i find a k7-smp kernel? i tried the same command with k7 in place of 386 and no dice. i even tried just finding a k7 kernel with the command sudo apt-get install linux-k7, but it coudn't find the package.


this seems like a nice distro, but i'm at school and don't have time to learnto recompile a kernel, so i'd like to get this issue resolved.

any input is greatly appreciated.

-Fedora Recovery

---

### Post by Fedora_Recovery on 2005-09-20
nobody? please??

---

### Post by serzz on 2005-09-26
There no such kernel as linux-386-smp. But yes you can install k7 based, type sudo apt-get install linux-k7-smp

---

### Post by simon w on 2005-09-28
I've only just started using Ubuntu, but use Debian at work.

If you've got apt-get, then try ```
apt-cache search smp
```

---

