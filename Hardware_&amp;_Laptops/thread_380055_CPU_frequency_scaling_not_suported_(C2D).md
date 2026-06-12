---
title: "CPU frequency scaling not suported? (C2D)"
date: 2007-03-09
forum: Hardware &amp; Laptops
---

### Post by alexmv on 2007-03-09
Hi,

Few days ago I bougth an Asus F3Jc laptop with a Core2Duo T5500 processor. On Windows XP the frequency of the CPU scales when idle/load from 999 Mhz to 1'6 Ghz, but in Linux (edgy, feisty) it says that "frequency scaling is not supported". 
When I type

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling

I get an error cos' /cpufreq doesn't exists, but dmesg reports 8 available states of scaling. Im using the latest bios available from Asus and the latest generic kernel from ubuntu.

Please, can someone help me?

---

### Post by teaker1s on 2007-03-10
After waiting to see if someone had a better answer than me:-

```
gksudo synaptic
```
Settings.>preferences>general
tick show package properties in main window.

these are choices that cover frequency scaling I found,  
[B]
cpudyn
cpufreqd
emifreq-applet
powernowd[/B]

search them read and decide what works for you, also you are running kernel for duel core as I'm guessing your processor is?

---

### Post by djscurippio on 2007-04-07
Same problem after upgrading to latest bios release (305) of 15 February 07.
Linux antani 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux

---

### Post by Adahn on 2007-04-07
> **alexmv said:**
> Hi,

says that "frequency scaling is not supported". 
When I type

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling

I get an error cos' /cpufreq doesn't exists, 
Please, can someone help me?



I get the same message on my A64.  FWIW, it didn't work in Edgy either.

---

### Post by teaker1s on 2007-04-07
amd 64
PowerNow
In order to take advantage of the various CPU clock states of the laptop, you should apt-get install powernowd and make sure that the frequency scaling and powernow modules are loaded in /etc/modules:
# CPU frequency
freq_table
cpufreq_userspace
# powernow
powernow-k8

---

### Post by Adahn on 2007-04-11
/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
 * CPU frequency scaling not supported


I get that error when running that apt-get command.  There is no 'module' folder in /etc either.

---

### Post by cprofitt on 2007-04-11
I am thinking of getting a new computer with a dual core processor... how does one know if they have a dual core kernel? I know there are 64bit downloads... are there dual core downloads for the install CD as well?

---

### Post by gloawu on 2007-04-20
Hi there!
I got Frequency Scaling (via powernowd) working again on my Thinkpad R60 (running x86_64 smp feisty) by removing "noapic nolapic" in /boot/grub/menu.lst from the boot parameters of my standard kernel. Now both cores are scaled to 1GHz when idle (Core2Duo T5600, max 1,86GHz). These two parameters must have been there from my edgy-installation from which i upgraded from since it refused to install without those back then. So just try to boot your system without those by pressing "e" at boot in grub an edit the "longest" line ;-)
If the system boots fine and Frequency Scaling works again, you can finally edit the boot parameters in grub to make the options permanent.
I hope this will help in your case too!

Since I'm busy right now: would be nice if someone could write that possible solution in the already filed bug report on launchpad

---

### Post by djscurippio on 2007-07-06
> **djscurippio said:**
> Same problem after upgrading to latest bios release (305) of 15 February 07.
Linux antani 2.6.20-13-generic #2 SMP Sun Mar 25 00:21:25 UTC 2007 i686 GNU/Linux

After few months of unsuccesful tries, i have found an [older BIOS image for my ASUS f3jc]("http://blog.scorpionworld.it/2007/07/06/asus-f3jc-frequency-scaling-and-old-bios-release/"). Now it's working again. ;)

---

