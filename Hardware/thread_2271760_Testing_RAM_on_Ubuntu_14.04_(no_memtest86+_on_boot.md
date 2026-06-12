---
title: "Testing RAM on Ubuntu 14.04 (no memtest86+ on boot menu)"
date: 2015-04-01
forum: Hardware
---

### Post by marco.cognetti on 2015-04-01
Hello,

I do not know if this is a redundant post, but I did not find the answer to my question checking other posts. In case, sorry. 

I installed Ubuntu 14.04.2 on my laptop. I would like to test my RAM. 
I usually do it through memtest86+, on the boot menu. This time, however, I do not have it in the grub menu (I have access to the grub menu but it displays just regular Ubuntu and its recovery mode), I guess this is due to some problems between systems with EFI and the software itself . 
I tried also with a LIVE CD but it is the same. It does not appear. I tried also to install the software on my Ubuntu and try sudo update-grub2, hoping that it will find it. 

I have to say the laptop has no problem, but it is just to be sure that the RAM is fine. Is there a way to install it? Or other ways to test the RAM?

Thank you,
Neostek

---

### Post by dino99 on 2015-04-01
maybe install or reinstall memtest86+
on the other hand, fwts is able to scan all the hardware and analyze/propose for found problem related to hardware

---

### Post by marco.cognetti on 2015-04-01
I tried to reinstall it but it does not seems to like it so much. Other ideas?

Neostek

---

### Post by weatherman2 on 2015-04-01
Can you temporarily choose "legacy" boot mode?   Sometimes you can do this in the firmware settings (aka "BIOS Setup").  If you can, then you'd be able to boot non-EFI from a live USB and get Memtest as a boot menu option again.

Sometimes you can simply choose a boot menu with a key like F12 at boot, and you can choose legacy boot devices there without even mucking with firmware/BIOS settings.  Your Ubuntu live USB might then show up more than once in the menu, once without EFI.

---

### Post by marco.cognetti on 2015-04-03
Just for infomation, I downloaded memtest86 from [here]("http://www.memtest86.com/") and mounted on a USB drive. It fully supports EFI systems, while memtest86+ seems to have some problems with that. Anyway, I run two passes of such a software on my RAM.

I guess it is healthy. Am I right?

Thank you,
Neostek

---

### Post by weatherman2 on 2015-04-03
If you are experiencing no issues with your laptop, then I'd say after two passes of Memtest your RAM is probably healthy.

Sometimes if people experience intermittent problems, running Memtest in a loop overnight can help find rare failures.  This seems not to be the situation with your laptop.

---

### Post by marco.cognetti on 2015-04-03
The test run for 6+ hours making 2 passes and half, founding no problem....
My laptop is new, I just wanted to be sure that the RAM is healthy. I will test it overnight but I guess it is 99% healthy. Since this test run successfully, I guess also the motherboard is fine. Otherwise, I would see some errors.

Am I right?

Thank you,
Neostek

---

### Post by weatherman2 on 2015-04-03
Yes, you are right, and I would not waste time running the memory test again overnight.

---

### Post by marco.cognetti on 2015-04-03
Ok thank you so much. It's time to enjoy my laptop.

Thank you,
Neostek

---

### Post by amerinde on 2015-04-04
anyway, yes, mentest is on the ubuntu install disk. at the first purple screen, at the bottom of the screen, u see a keyboard + (someother symbol) hit the arrow key down, then u will get the main screen, and can choose what u want.

---

### Post by weatherman2 on 2015-04-04
> **amerinde said:**
> anyway, yes, mentest is on the ubuntu install disk. at the first purple screen, at the bottom of the screen, u see a keyboard + (someother symbol) hit the arrow key down, then u will get the main screen, and can choose what u want.

Your are describing a "legacy" (non-EFI) boot of Ubuntu.  When you boot via secure boot/EFI, you don't get that same purple screen - instead, you get a menu...which does not include Memtest.  It looks like the screen shot on this page:

[http://askubuntu.com/questions/208405/how-to-efi-install-ubuntu](http://askubuntu.com/questions/208405/how-to-efi-install-ubuntu)

---

### Post by marco.cognetti on 2015-04-06
I confirm what weather2 said: for EFi system you have exactly the screenshot he/she posted. That is the reason for which one has to download memtest from its website and boot it from a USB stick. This is one easy way for testing the RAM with EFI system.

Thank you,
Neostek

---

