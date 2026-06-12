---
title: "asus GT520 woes"
date: 2011-12-05
forum: Hardware
---

### Post by g-man30 on 2011-12-05
Hello, today i purchased the aforementioned graphics card with the hope of it working... it seems i was wrong with the card installed ubuntu will not boot (goes past the grub and then gives me a purple screen then a grey/black screen) after un-installing the card it boots first time. 

any help will be appreciated, please bare in mind that i am not massively technical when it comes to PCs though 

oh i am running 11.10 btw

thank you

---

### Post by gordintoronto on 2011-12-05
Most people would call this card an Nvidia GT520, made by Asus. It should work very nicely in any version of Linux.

When the card is not installed, what provides video on your computer? Open Terminal and enter this command: lspci

It should produce around a dozen lines of output, and one of them will contain the text "VGA." That's your current video adapter.

Did you install a specific driver for your video adapter? If so, remove it and then install the GT520. I think you can run "Additional Drivers" to check, and to remove, the driver which you no longer need.

You might need to "disable the on-board video in your BIOS." If you don't understand that, don't worry about it just yet.

I assume you moved your monitor cable from the old connection to the new video card....

You could also mention what brand and model your computer is.

---

### Post by g-man30 on 2011-12-06
Hi thanks for the response, the computer is made of parts,
 it is an ecs nvidia motherboard with an AMD Athlon(tm) II X4 630 Processor, graphics are GeForce 6150SE nForce 430/PCI/SSE2 (onboard)

the monitor cable was in the card while i was trying

---

### Post by g-man30 on 2011-12-06
I have sorted this problem now....it was caused by me being thick... i forgot changed the drivers to an older version to make it run before.... sorry for being a dumb *** and waisting your time

---

### Post by gordintoronto on 2011-12-06
Not a problem. Most people make much bigger mistakes. I hope my post helped trigger your memory.

---

