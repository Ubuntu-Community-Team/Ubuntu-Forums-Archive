---
title: "i686smp kernel?"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by LoloftheRings on 2009-04-08
Hi all,

I've been running a i386 kernel for a while, but I have a Pentium 4 with HT. I guess my system would be faster when running i686smp, but I have no idea where to find the kernel. I've been looking on kernel.org, but couldn't find it. Do I have to install the latest kernel with specific compile parameters?
I'd be great if I could install the kernel through a repository, so it will be updated automatically.

Another thing, little off topic. My processor is often overheating when running at normal speed (3Ghz). I have to set it to 2.5Ghz to make it stable. When running at 3Ghz, it freezes at about 60 degrees Celcius (not that hot, right?). Can a new processor cooler fix this?

Thanks in advance,
Robert

---

### Post by impediment on 2009-04-08
I have similar situation but with 2 32bit pent4's and hyperthreading.  If you find a repository please post your findings.

---

### Post by manuelg on 2009-04-08
You'll need to recompile your kernel for i686 smp.  There are several good guides floating around.  Just do a google, "ubuntu compiling kernel" something like that.

---

### Post by LoloftheRings on 2009-04-09
After following this guide [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html) I get an error message about my wireless drivers I guess during
```

make modules

```

scripts/Makefile.build:231: target `ubuntu/../drivers/staging/rt2860' doesn't match the target pattern
scripts/Makefile.build:231: target `ubuntu/../drivers/staging/rt2870' doesn't match the target pattern
  Building modules, stage 2.
  MODPOST 2292 modules
WARNING: modpost: Found 6 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'


I have a wireless card, drivers are working great atm. Is there any way to exclude the wireless from the make modules command?
I'm using 802.11 WiFi with WEP encryption. current driver is rt61pci.
I used 'make menuconfig' to configure the kernel.
Source downloaded using
```

sudo apt-get install linux-source

```

I'm trying not to break my system, but if it happends, I do have a backup :p

Thanks for quick reply

---

### Post by LoloftheRings on 2009-04-09
I was just looking at some benchmark and system analyzer and it's telling me this:
Kernel	Linux 2.6.28-11-generic (i686)
Compiled	#40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009
C Library	GNU C Library version 2.9 (stable)
Distribution	Ubuntu jaunty (development branch)

Does this mean I already have an i686 SMP or is it just my processor type?
uname -a returns:
Linux robert-desktop 2.6.28-11-generic #40-Ubuntu SMP Fri Apr 3 17:39:51 UTC 2009 i686 GNU/Linux

---

### Post by LoloftheRings on 2009-04-09
Ok, after a long time of waiting and compiling (about 3 hours I guess), I ran make install, finally, but I'm not sure if it really installed the kernel into the /boot directory. The kernel I'm booting right now, is a -generic kernel. Also, when I check the date the kernel was modified, I see that it is yesterday, while I built the kernel today.
Anything went wrong during make install?

---

### Post by LoloftheRings on 2009-04-09
Alright, I'm finally running my compiled kernel!

I'll tell what I did in order to make it work:

First of all, get the kernel source:
```
sudo apt-get install linux-source
```
Then, follow this guide:
[http://www.cyberciti.biz/tips/compil...kernel-26.html](http://www.cyberciti.biz/tips/compil...kernel-26.html) 
But.. Do not run mkinitrd but mkinitramfs. If Ubuntu isn't installed on hd(0,0), or hda0/sda0, you have to pass a -r option.
My Ubuntu installation is on sda1, which is 1,0. I used the following mkinitramfs command:
```
mkinitramfs -r 0,1 -o initrd-2.6.28.9 2.6.28.9
```

That was pretty much it, although I had some problems.. This is actually the first time I compiled a kernel myself so I'm not that experienced.

Solved!

---

