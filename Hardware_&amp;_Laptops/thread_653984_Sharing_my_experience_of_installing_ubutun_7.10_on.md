---
title: "Sharing my experience of installing ubutun 7.10 on HP  Pavilion tx1000"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by Jasmineflower on 2007-12-30
I am a little bit unlucky, to install ubuntu on my computer is absolutely not easy. Finally, I made it. I guess other people with the similar laptops must have the same questions as me. Hope my post can help them.

I tried wubi, does not work on my laptop. I guess it is because I have to add boot parameter noapic which is not supported by wubi. Besides, After I uninstalled the wubi, I lost some space on my hard drive. Some posts say the Disk Defragmenter can fix it. I am not sure, 

First, to burn the Live CD. the CPU of mine is AMD Turion 64 X2. I choose the i386 32bit release since the hardware information on the control panel of my Windows Vista shows my CPU is 32 bit. Based on the description of 64 release, I guess 64 bit release works too. Maybe I will try that later.

Second, boot into the live CD, at the boot menu press F6 and add noapic at the beginning of the command line

Third, install the ubuntu, click installer on the desk, it will ask several questions. When it proceeds partition, I choose the option manual, but I am not prompted anything in the following process. I also tried the guided options, no response, then I choose manual.

Fourth, install the wireless card, To active the fireware, System->Software Sources, check all the items on the tag Ubuntu Software and Third-Party Software. Go to the System->Restricted Driver manager enable Fireware. My wireless card is BCM4311 Rev 02 The only way to install it is, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

