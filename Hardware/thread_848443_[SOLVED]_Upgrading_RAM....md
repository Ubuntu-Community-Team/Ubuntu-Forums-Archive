---
title: "[SOLVED] Upgrading RAM..."
date: 2008-07-03
forum: Hardware
---

### Post by SeanLor on 2008-07-03
Greetings!

So, this isn't exactly an Ubuntu-related question, but the community has been so helpful thus far. I figured it couldn't hurt to ask, and at the very least you cats can point me in the right direction.

I picked up some new RAM for my Dell Inspiron 1525 laptop, and although it should be compatible & there's no problem with the 2 ram slots, my computer will not recognize the new modules. With both installed, the computer will not boot, and with one new & one old installed it only recognizes the old module. When purchasing the modules, I made sure that they matched the specs that Dell recommended. I've already flashed the BIOS, and still no go. Any suggestions, comments, help would be greatly appreciated - I realize that there's a chance the modules are crap, but I need to determine if it's a problem on my end before I rattle my sabre & return/exchange them. Thanks so much!

Trying to install: SAMSUNG 4GB DDR2 SODIMM 4 GB PC2 PC 5300 667Mhz 2 X 2GB

---

### Post by zgornel on 2008-07-03
Are you sure the computer supports 4GB ?

---

### Post by SeanLor on 2008-07-03
I'm about 95% sure; it's two slots can each support 2GB, and I checked memoryexpress.com's recommendations & a couple other places.

---

### Post by zgornel on 2008-07-03
How many modules do you have in total ? One new and one old, two new and one old or ... ? Try the new modules one at a time and see if they can be recognized. Also, try all the possible combinations between them (including changing the slots). Go here [http://en.wikipedia.org/wiki/List_of_Intel_chipsets](http://en.wikipedia.org/wiki/List_of_Intel_chipsets) and check that your chipset supports maximum of 4GB of ram (this is probably the case but you can never be too sure). This might not be important but, when changing the ram modules, remove the laptop battery before doing any change whatsoever. Good luck !

---

### Post by SeanLor on 2008-07-03
I've got two new modules, and my laptop came with two 512Mb modules. Unfortunately I tried all the combos - both new, one old & one new, and vice versa to make sure it wasn't a problem with the slots. I'll double check the chipset when I get home in a couple hours, thanks for the link!

---

### Post by Kevbert on 2008-07-03
What type of OS are you using ?  If it's 32 bit you'll never see much more than 3.2Gb due to address limitations.  Same thing if the processor is only 32 bit.
The other thing you could check is if there's any BIOS protection stopping you from reconfiguring.

---

### Post by SeanLor on 2008-07-03
I'm using Ubuntu Hardy w/ Vista home basic, 32 bit, dual-booted. I'm really not very tech-savvy, how would one go about checking whether there's BIOS protection?

---

### Post by SeanLor on 2008-07-03
I don't think there's anything BIOS-wise preventing a different system configuration; when I had one 2GB module & one of the original 512Mb installed, it recognized that the amount of system memory had changed but only recognized the 512Mb.

---

### Post by zgornel on 2008-07-03
Well, do not worry, the problem is not the OS. Even if Ubuntu would not see all the 3.2 GB, the computer would function perfectly normal. Try entering bios (obviously with the old ram installed) and look for any suspicious options ... whatever those might be. Consult the DELL technical booklet for changing ram and bios configuration options (there are only a few on laptops anyway).

---

### Post by StormPCs on 2008-07-05
Dell doesn't provide BIOS options in their computers really, not even the desktops.  It's not the BIOS.  Yes, the 1525 can use 4GB but you should go with Dell's recommendation as they can be finicky.

My money is on the motherboard being faulty.  If that's not it then it's the memory modules or user error.

If you tried the new modules individually and neither worked then it's likely the motherboard.

---

### Post by SeanLor on 2008-07-11
Thanks for the help, folks. Turns out I was shipped two DDR1 modules, picked up the proper bits & I'm all set. =D

---

### Post by zgornel on 2008-07-11
> **SeanLor said:**
> Thanks for the help, folks. Turns out I was shipped two DDR1 modules, picked up the proper bits & I'm all set. =D

:D Who would have thought ...

---

### Post by SeanLor on 2008-07-12
I figured I'd exhaust my resources before returning the modules & rattling my sabre; thanks again for the suggestions. :) Here's hoping the seller is decent about the return - I'd rather attribute it to human error than malicious intent.

---

### Post by ljonesj on 2008-07-12
wild those ddr1 modules should not have even been able to to fit in a ddr2 slot as the keys are in a different places on the ram

---

