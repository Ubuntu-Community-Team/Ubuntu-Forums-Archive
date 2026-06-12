---
title: "VIA EPIA cpu freezing - libc6-i686?"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by georgek on 2005-10-20
I'm suffering from my box freezing every so often.  One possible cause I'm wondering about is the use of libc6-i686.

I tried the 686 kernel on this box but it wouldn't boot and I found a forum post that confirmed that this processor won't run the 686 kernel (missing cmov from its capabilities if I remember right).  That's fine, I can live with a 386 kernel.

I see that libc6-i686 is installed.  Reading the description in synaptic it's used only if a 686 processor is detected at boot.  It suggests checking using uname.  When I do this I get:

$ uname -a
Linux manuel 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux

This makes me suspect that the i686 libraries are in use.  If I want to remove them, I also have to remove ubuntu-minimal.  Now having struggled with an upgrade on another box because I had removed packages which led to ubuntu-desktop being removed, I'm nervous.

So, finally, my questions:

How can I check for sure which version of libc6 is in use?

How risky is it to remove ubuntu-minimal?

Does anyone know for sure if I can run 686 libs on this processor:
$ cat /proc/cpuinfo
processor       : 0
vendor_id       : CentaurHauls
cpu family      : 6
model           : 7
model name      : VIA Samuel 2
stepping        : 3
cpu MHz         : 400.416
cache size      : 64 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu de tsc msr cx8 mtrr pge mmx 3dnow
bogomips        : 792.55

Thanks for any help.

---

### Post by Lem on 2005-10-20
As far as I'm aware the fanless Epias don't have cmov support and won't run a 686 kernel. 
I have a M10K and run a 686 kernel, but a 386 kernel on my M2-6000E

---

### Post by georgek on 2005-10-20
Lem, I can confirm that I can't run the 686 kernel.  I'm wondering about libc.

Since posting the first post, I've found various crash threads and I'm trying with powernowd disabled.

Before I disabled it, I had one crash without the 686 libc so it doesn't look like that's the whole answer.  I did have a look at the package contents though and most of the libs were in a path which included "cmov".  This makes me suspect the 686 libs *shouldn't* work with this processor.

It would still be good to hear from someone who knows though. :)

---

### Post by lynrees on 2005-10-24
Hi,

I also have problems with breezy:

I have an epia M9000 which freezes quite regurlarly when I do things with USB, but freezes occasionaly anyway. The M9000 is of the VIA Ezra CPU variety, which does not support i686, and I therefore run only a i386 kernel.

I also had a Nehemiah M10000 board, which is i686 compatible but had exactly the same problem! 

I have installed another OS (slax on the hard drive) to another partition and all is fine. Warty also worked perfectly well before I upgraded (fresh install).

Anybody have anyideas?

---

### Post by jerryf70 on 2005-11-23
Me too.  Via Epia M9000.  Hoary worked fine (still does), Breezy freezes intermittently.  Seems to happen a lot when using Synaptic, but sometimes occurs when idle.  Have installed Breezy from same disk on Dell laptop with no problems, so is obviously hardware based.  Any advise welcome.

---

### Post by jerryf70 on 2005-11-26
Okay, sussed it.  For future reference what fixed it for me was disabling longhaul.  Adding the following to /etc/modprobe.d/aliases did the trick:

alias longhaul off

Hope this helps somebody.

A good site for these issues is:

[http://epialinux.org/](http://epialinux.org/)

---

### Post by Mujaheiden on 2005-12-08
Thanks so much... keeping my fingers crossed.... ive been looking for such a long time for this info. But what does longhaul do (did)?

---

### Post by axelb on 2006-04-07
Thank you!

This saved me from my continously freezing Machine :-)

I have a VIA C3 (silent!) cpu with 700 mhz. Mainboard: MSI 694T pro.

I noticed it happend with no particularly intervalls, so I suspected some system process to be the culprit here. The only pattern I could find, was that when the workload improved or decreased, my machine would possibly freeze totally, so this also fits nice in with the disabling of scaling the cpu speed.

The problem first started when I upgraded from Ubuntu 5.04 to 5.10, so longhaul must be disabled in my old kernel, but not in the new one. 
- This just for the case someone else should have the same problem and need some more clues :-)

Best regards Axel Bojer

---

### Post by domthom on 2006-04-19
thank you jerry!
The 
alias longhaul off 
entry and a reboot fixed it for my model name : VIA Samuel 2 machine

---

