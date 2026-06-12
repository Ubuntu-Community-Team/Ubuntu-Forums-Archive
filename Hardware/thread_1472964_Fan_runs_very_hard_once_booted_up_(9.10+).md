---
title: "Fan runs very hard once booted up (9.10+)"
date: 2010-05-04
forum: Hardware
---

### Post by rojodojo on 2010-05-04
Hello,

First, the model of my laptop is the [HP DV6607nr]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c01278427&dlc=en").

I've had this weird problem with Ubuntu 9.10 and 10.04 where after I boot to the desktop, the fan (I presumably for the CPU) starts running excessively for about 5 minutes. I have nothing loading up at all on my bootup, in fact I've taken out everything I don't need in my laptop (printer, compiz, ubuntu one, etc). I've looked at the System monitor and the data at the startup is no different than one hour later; my two CPUs run at about 5-10% load and the ram used is >200mb. 
This oddity never happened in Ubuntu 9.04. Also, I will add that this fan problem occurs if I boot windows Vista, 7 but not XP.

Any help would be great,

Thanks in advance

---

### Post by bsmith1051 on 2010-05-05
So you've got a laptop which you've tested with all those different OSes:

WORKS OK
- Ubuntu 9.04
- Windows XP

DOES NOT WORK OK
- Ubuntu 9.10
- Ubuntu 10.04
- Windows Vista
- Windows 7

And, your processor is a Mobile Athlon X2 (TK53).

The really key question is what motherboard/chipset does it use?  The HP support pages says it has an Nvidia 7150 GPU (good choice!) so presumably it has an Nvidia motherboard, too.  

Do you know if this is one of the models that suffers from overheating?  It may be that the old OSes don't properly recognize the overheating and therefore don't ramp-up the fan like they should.  Whereas the newer OSes *do* recognize that there's a problem and run the fan on High to try and prevent damage.  

Also, do you know what BIOS version you have, and if it's the latest?

Honestly, I would call HP tech support and ask them about both the BIOS version and the Nvidia overheating problem -- they probably owe you a replacement motherboard??

---

### Post by rojodojo on 2010-05-12
I tried updating the bios to no avail and my laptop's 2 years old so it's not covered by any warranty anymore.
I decided to just run it on what works most efficiently, even if it means using dated operating systems. I disabled/removed the flashy stuff from 7 and lucid lynx anyways.

---

