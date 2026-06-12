---
title: "HP Pavillion a6400f"
date: 2008-05-04
forum: Hardware
---

### Post by mcpetersen.dsm on 2008-05-04
Has anyone had luck installing 8.04 on the HP a6400f? The 64-bit installation CD seems to hang a few moments after being given the instruction to install.

---

### Post by mr tobin on 2008-05-04
I don't have a a6400f, my Pavilion is a dv2000 but it installed no sweat... Just neither the Windows Wireless Adapter nor my graphic adapters installed. 

Did you try installing from windows or did you load the disc on system start up?

---

### Post by mcpetersen.dsm on 2008-05-04
> **mr tobin said:**
> I don't have a a6400f, my Pavilion is a dv2000 but it installed no sweat... Just neither the Windows Wireless Adapter nor my graphic adapters installed. 

Did you try installing from windows or did you load the disc on system start up?

I booted using the Ubuntu installation CD. I'll try from within Windows.

---

### Post by mcpetersen.dsm on 2008-05-04
It seems to make no difference whether it boots from the CD or within Windows. It freezes while starting.

---

### Post by Ayuthia on 2008-05-05
Do you know if you have an AMD chip with Nvidia graphics card?  If so, you might try to use noapic when starting up.  When the boot screen appears, press F6 and add noapic to the end of the line and press enter.  It should boot up for you.  This happens for some HP users with this combo.

---

### Post by mcpetersen.dsm on 2008-05-05
Thanks for the suggestion, Ayuthia, but no success. Here are some of the specs:
Processor
 Intel® Pentium® Dual-Core Desktop Processor E2200 
&#8226; 2.20 GHz, 1MB L2 Cache, 800 MHz Front Side Bus 
 
Chipset
 Intel® G33 Express Chipset
 
Standard memory
 3072 MB (2 x 1024 MB; 2 x 512 MB)
 
Memory type
 PC2-6400 DDR2 SDRAM
 
Video adapter
 Intel® Graphics Media Accelerator 3100

---

### Post by u_i_we_all_buntu on 2008-05-16
I also have the HP a6400f and I'm also having problems.  

However, I'm not installing the 64bit version. I know that the Intel E2200 is an "Intel 64" chip, but I was told that it's still basically a Pentium.     Thanks for the heads-up that the 64-bit version is causing your a6400f to hang. I won't go that route.

I created a 32bit Ubuntu 8.04 desktop boot CD, and it booted with ONE problem:  I can't get the network interface to work.  I've tried numerous automated and manual approaches, and I can't get the network running.  Everything else seems to work.

I googled "a6400f linux" and found that everyone trying to install linux on a6400f is having trouble with the network card.  One user got around the problem by installing a supported network card.  
(see: [http://www.nabble.com/rtl811-8168-td16829263.html](http://www.nabble.com/rtl811-8168-td16829263.html) ).

... I should have checked in the ubuntu certified systems list before getting this a6400f.  It's a real crappy system running Vista.  1Gig of RAM is committed as being used while doing nothing.  

If I can't get Linux running on thie box, I'll install XP.

Good luck!

---

### Post by Snyper_Vash on 2008-05-16
Im having problems with my dv9008nr. Seems like wireless might be a pain.

---

### Post by mcpetersen.dsm on 2008-05-17
I finally got the a6400f to work by installing the 32-bit version. Networking was a problem until I simply reverted to Ubuntu's default for roaming but entered my ISP's DNS server IP addresses, turned it off and went to bed. The next morning, no problems.

---

### Post by alguin2 on 2008-05-27
***The solution below really works for the HP a6400f.***

1. Install 8.04, because the fix below works specifically with 8.04 (2.6.24-16-generic)
2. Follow the fix posted by AgDon92 at: 
[http://ubuntuforums.org/showpost.php?p=5002506](http://ubuntuforums.org/showpost.php?p=5002506)

It worked for my HP a6400f PC with 3Gb RAM, 500Gb disk, Dual-core 2.2Ghz Intel E2200.  The machine is now a real pleasure to use, running Ubuntu 8.04 with full gigabit network capability.

Enjoy.

---

