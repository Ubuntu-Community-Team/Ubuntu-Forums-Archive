---
title: "[SOLVED] cpu scaling 6.10"
date: 2008-12-27
forum: Hardware
---

### Post by flyingsliverfin on 2008-12-27
how do i scale my CPU speed (I want to tune it down to 500 MhZ TEMPROARILY)

is there a easy terminal way to do it?

(I like terminal, so im trying to learn everything I can about it)

---

### Post by Rocket2DMn on 2008-12-27
Hi, you're thread title says 6.10, which is an old and unsupported version of Ubuntu called Edgy Eft.  CPU scaling has improved significantly since that version and should work out of the box, so if that is indeed the version you have, you need to upgrade to a supported version of Ubuntu (preferably 8.04 Hardy Heron which is a LTS release, or 8.10 Intrepid Ibex).
What is the processor in the machine?  Not all processors support scaling, esp. older ones.

---

### Post by flyingsliverfin on 2008-12-28
well i'd like to upgrade but it doesn't work see my thread at:
[http://ubuntuforums.org/showthread.php?t=1017037](http://ubuntuforums.org/showthread.php?t=1017037)

i think it's an INTEL chip though

dont know exactly how to find what version of chip is in this laptop...


im on vacation and have my dads old ancient laptop for the trip to do homework, so i might not always have internet: it might take  a while to reply.

thanks for replying though

---

### Post by Rocket2DMn on 2008-12-28
A user in that other thread linked you to this wiki page, which is useful - [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
There is a section called "Installation without a CD" which is your best chance to do a fresh install (you can't upgrade the current version since 6.10's successor is also unsupported now).  You will likely want to try an install from a USB stick, or if possible, even a network install.  I'm afraid I haven't done either of those myself.
Check the boot order in your BIOS and see what options you have for media other than your hard drive to boot from.

---

### Post by sdennie on 2008-12-28
You can find out your chip information with:

```

cat /proc/cpuinfo

```

You can find out if CPU scaling is available using:

```

sudo apt-get install cpufrequtils
cpufreq-info

```

Most chips don't support arbitrary speeds but instead have a range of speeds that can be used.  Generally, if Ubuntu detects that you have a chip where CPU scaling is appropriate, it will use the ondemand CPU governor and your CPU will automatically scale between the lowest supported speed and the highest.  This is good for the machine and it's generally not possible for the user to notice the CPU scaling.

---

### Post by Coder543 on 2008-12-28
Seriously, try this.
> **Partyboi2 said:**
> You will probably need to add
```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ edgy-security main restricted universe multiverse 
``` to your sources.list before trying to upgrade.

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades)

---

### Post by flyingsliverfin on 2008-12-28
I did try to add that, but it didn't work, I might have found a way to upgrade though using the manual install. (well it didn't really work, but when I changed all the things in the 'sources.list' to 'feisty' it seems to be able to upgrade a bit. It only to tried to update some things, then said that the system is up to date and is trying to upgrade currently.

here is the chip info

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 11
model name      : Mobile Intel(R) Pentium(R) III CPU - M   866MHz
stepping        : 4
cpu MHz         : 866.000
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 1728.45


that might help right?

currently trying to upgrade so I can't use 'apt' for 

sudo apt-get install cpufrequtils
cpufreq-info

oh, I didn't see the net install. And the bios can't be accessed that easyliy. I can, and there is no option from USB. Need to try the one with a seperate partition to house CD image and the one from net.(if the one that im trying right now doesn't work.

---

### Post by flyingsliverfin on 2008-12-29
SOLVED

I've been SOOOOOO dumb. I didn't even add a CPU Frequency Scaling Monitor!!!!! now I can scale it between 400Mhz and 866MHZ. (This an ancient laptop)

thx for all ur replies!!!!

stupid,stupid,stupid,stupid,stupid,stupid,stupid,stupid,stupidstupid,stupid,stupid, ME

---

