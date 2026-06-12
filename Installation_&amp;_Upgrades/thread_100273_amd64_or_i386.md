---
title: "amd64 or i386"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by PhilOSparta on 2005-12-07
I have a new AMD64 and by mistake I loaded an i386 install iso onto it.
It is working okay, but there are a few problems.
The clock applet is running twice as fast as it should and the system monitor panel applet indicates that the CPU is running at 50% when the real system monitor application indicates 2%.

Should I uninstall the i386 version and load the AMD64 version?
Any advice would be appreciated.

I have Ubuntu on a P3 and a P4.  This is my first AMD64.:)

---

### Post by Pablo_Escobar on 2005-12-07
Firstly:
1. Double-clock problem : Here is the whole discussion regarding this problem : []("http://ubuntuforums.org/showthread.php?t=53094&highlight=double+clock")

2. I have a AMD64 and I run 32bit :)

You have to ask yourself a question - am I profficient and skillfull enough in Linux to work with some problems that 64-bit version is known to have ???
I for one have to get more current with chroot, to try out the 64-bit version.

---

### Post by PhilOSparta on 2005-12-07
[QUOTE=Pablo_Escobar]
1. Double-clock problem :  [http://ubuntuforums.org/showthread.php?t=53094&highlight=double+clock](http://ubuntuforums.org/showthread.php?t=53094&highlight=double+clock)


work with some problems that 64-bit version is known to have ???
I for one have to get more current with chroot, to try out the 64-bit version.[/QUOTE]

Pablo - Thanks for your info.  The fix worked perfectly.
I guess I have to research the "problems" and the need for chroot.
Your suggestions will lead me to further knowledge.
Thanks again,
Phil

---

### Post by Robocoastie on 2005-12-07
Hi Philososparta and welcome to Ubuntu.

The problems in 64 bit are due to multimedia applications not being written for it yet particularly windows codecs and flash. There is some solutions for flash but I've found its spotty some sites just refuse to work with anything than the official flash plugin. 

I have found however that Crossover Office Standard demo DOES work with 64bit Ubuntu and thus gives you MSFT Media Player plugin for your news sites but I think its only version 6. This doesn't however, give you the codecs for making your own windows codec based mutlimedia. Many other programs are written only for 32 bit libs as well and the way around that is installing a chroot enviornment. I've found other problems too - some things like opengl games linux games won't produce sound in 64 bit whereas I get it in 32 bit version. 

So it depends on what you want your linux use to do (like all things *nix IMO).

---

### Post by PhilOSparta on 2005-12-08
Thanks for your insight.  I think I will stick to the i386 version for now since everything seems to be working for the apps that I use.   Most of my work is photo processing, web browsing and printing.  What little use of flash in browsing seems to work.

Maybe as the 64 bit drivers become available I'll convert over to the 64 bit kernel distro.

Thanks again,
Phil

---

