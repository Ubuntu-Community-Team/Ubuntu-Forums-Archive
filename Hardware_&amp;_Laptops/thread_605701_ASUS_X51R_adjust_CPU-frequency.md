---
title: "ASUS X51R adjust CPU-frequency"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by equimet on 2007-11-07
Hello there,

because of the fact that noone in the german ubuntuforums could help me I'm trying the best here ;-)
My problem is that I cannot change the CPU-frequency of my Notebook and so it's consuming more power than it should. I went through tutorials but none of them worked for me.
At first I tried to add the CPU-frequency-applet to the gnomepanel, but it said that CPUfrequency is not supported. So I changed the rights of /usr/bin/cpufreq-selector via > chmod +s /usr/bin/cpufreq-selector and started **cpufreq-selector** in a terminal, but it just said >  No cpufreq support .

There must be a way to adjust the coufrequency, because when I'm working on my windowsXP the CPU's keep running on 700Mhz.

Additionally some informations that may help you:
**cat /proc/cpuinfo**
Nopaste-link --->[http://ubuntuusers.de/paste/17639/](http://ubuntuusers.de/paste/17639/)

**uname -r**
2.6.22-14-generic   

I hope there is someone that can help me ;-)

equimet

PS: Excuse my bad english

---

### Post by Gag_Halfrunt on 2008-02-18
> **equimet said:**
> 
PS: Excuse my bad english
Macht nichts, meines ist auch nicht gut ;-)

Please have a look at this post: [http://ubuntuforums.org/showthread.php?t=617860]("http://ubuntuforums.org/showthread.php?t=617860")

---

