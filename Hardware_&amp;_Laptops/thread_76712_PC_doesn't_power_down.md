---
title: "PC doesn't power down"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by caspar_wrede on 2005-10-15
I have installed ubuntu breezey on a very old computer for my sister. The problem is that after telling the computer to shutdown (via GUI or command line) it does so but then immediately boots up again.

Here is the cpuinfo
```

model name      : Celeron (Mendocino)
stepping        : 5
cpu MHz         : 400.981
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat p
se36 mmx fxsr
bogomips        : 794.62

```

Any ideas?

---

### Post by gsaathoff on 2005-10-15
possibly this is a BIOS issue?  have you checked BIOS setup for power options?

also, have you tried this function with another distro / os?  if so, what happens?

---

### Post by caspar_wrede on 2005-10-15
[QUOTE=gsaathoff]possibly this is a BIOS issue?  have you checked BIOS setup for power options?

also, have you tried this function with another distro / os?  if so, what happens?[/QUOTE]

I just had a look at the bios but could see nothing suspicious. Also I am not really a bios guru.

It worked with Windows 98 which was installed on the computer before ubuntu.

---

### Post by gsaathoff on 2005-10-15
Maybe this will help?

[http://ubuntuforums.org/archive/index.php/t-5193.html](http://ubuntuforums.org/archive/index.php/t-5193.html)

Good luck,

-g

---

### Post by zootreeves on 2005-10-15
Same problem for me on a thinkpad R32

---

### Post by daschl on 2005-10-15
[QUOTE=caspar_wrede]I just had a look at the bios but could see nothing suspicious. Also I am not really a bios guru.

It worked with Windows 98 which was installed on the computer before ubuntu.[/QUOTE]


is the system AT or ATX?

because maybe it has something to do with the automated power down - witch is supported under atx.

i suppose that windows 98 said "you can now turn off the computer" in this nice-looking orange blinky-blinky letters? ;)

---

### Post by az on 2005-10-15
Open a terminal and type dmesg

Post all the output here and it will show (among other things) the details of how your kernel is handling power management.

---

### Post by caspar_wrede on 2005-10-17
Thanks for all your help. I tried everything and it just didn't work.

Then I did something terrible. I was sick of all the time i was spending on trying to getting the damn thing to work and sick of my sister complainging that she didn't have an adequate version of MSN messenger. So I installed windows 2000.

And the really shocking thing was that it is SO MUCH faster and snappier than ubuntu!!! A tale of linux failure, sadly.

Caspar.

---

