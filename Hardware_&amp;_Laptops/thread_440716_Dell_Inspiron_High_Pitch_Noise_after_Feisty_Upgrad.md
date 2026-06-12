---
title: "Dell Inspiron: High Pitch Noise after Feisty Upgrade"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by jyotishman on 2007-05-11
Hi,

I upgraded today from Edgy to Feisty, and turns out that I am encountering a new problem: I can hear a very high pitch/frequency noise coming out of my laptop (Dell Inspiron E1405, Core2 Duo). I have had this same problem previously, but in Windows XP, and the following trick worked:

My problem (in XP): [http://forum.notebookreview.com/showthread.php?t=102907](http://forum.notebookreview.com/showthread.php?t=102907)
Proposed solution: [http://forum.tabletpcreview.com/showthread.php?t=3516](http://forum.tabletpcreview.com/showthread.php?t=3516)

I am wondering if there is some solution for Feisty as well? I never encountered this problem before while using Edgy. 

Thanks in advance.

- Jyoti

---

### Post by ghostboy on 2007-05-15
> **jyotishman said:**
> Hi,

I upgraded today from Edgy to Feisty, and turns out that I am encountering a new problem: I can hear a very high pitch/frequency noise coming out of my laptop (Dell Inspiron E1405, Core2 Duo). I have had this same problem previously, but in Windows XP, and the following trick worked:

My problem (in XP): [http://forum.notebookreview.com/showthread.php?t=102907](http://forum.notebookreview.com/showthread.php?t=102907)
Proposed solution: [http://forum.tabletpcreview.com/showthread.php?t=3516](http://forum.tabletpcreview.com/showthread.php?t=3516)

I am wondering if there is some solution for Feisty as well? I never encountered this problem before while using Edgy. 

Thanks in advance.

- Jyoti


Install Kmix.  Application>Add/Remove>Search for Kmix.  If it is not installed, install it.

Run Kmix.  Alt+F2 type Kmix.  When the Kmix windows opens, make sure that your Output options are turned on and then adjust them as you need.

---

### Post by jyotishman on 2007-05-19
> **ghostboy said:**
> Install Kmix.  Application>Add/Remove>Search for Kmix.  If it is not installed, install it.

Run Kmix.  Alt+F2 type Kmix.  When the Kmix windows opens, make sure that your Output options are turned on and then adjust them as you need.

Hi -- thanks for your suggestion. I tried it, but no use. Actually, I do not think it is the problem with the speakers. It has more to do with the processor itself. I had the same problem with my Windows XP, and the following solution solved it: [http://forum.tabletpcreview.com/showthread.php?t=3516](http://forum.tabletpcreview.com/showthread.php?t=3516)

Not sure if something similar can be done for Fiesty :rolleyes:

---

### Post by Sukarn on 2007-05-19
I've had the same problem in Edgy, then the problem spread and it became so that if I did not close esd by going into first terminal, X would not even go to the splash screen. closing esd essentially cut off all my sound, and after that my sound hardware stopped being detected (the problem with esd continued). Then I started facing problems with my graphics, and right now I've got Ubuntu sitting on a 6GB partition of my hard drive without having been booted for about 2 months while I'm using XP without any problem.
It all started after I got a new motherboard (my old one got fried).
Linux hates my motherboard... I've given up on using any Linux distro till I get a new PC.

---

### Post by jyotishman on 2007-05-19
Actually, I applied a solution suggested at: [http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises](http://www.thinkwiki.org/wiki/Problem_with_high_pitch_noises)

Here is it: "(On Ubuntu 5.10, the default kernel uses processor as a module. Unfortunately, the script loading it, /etc/init.d/acpid, ignores the options processor max_cstate=3 setting in /etc/modprobe.d/<my file>. As a solution for this specific problem, add the line echo 2 > /sys/module/processor/parameters/max_cstate directly to /etc/init.d/acpid, at the end of the function load_modules(), immediately after the line echo "$PRINTK" > /proc/sys/kernel/printk.)"

And the "magically" the noise has disappeared !! :)

---

