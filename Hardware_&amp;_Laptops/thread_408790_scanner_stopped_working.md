---
title: "scanner stopped working"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by adyeths on 2007-04-13
I seem to be having problems getting my scanner to work now in Edgy. Its a Plustek OpticPro UT24 usb scanner. It used to work without any trouble, but now the scanner does not seem to be detected properly.

When I try running **xsane** it pops up a window saying its scanning for devices but then quits without giving me any kind of information whatsoever. I tried running it from a terminal window to see if it would provide any error messages but still nothing.

When I open a terminal and type lsusb it shows the scanner is there...
*Bus 001 Device 010: ID 07b3:0017 Plustek, Inc. OpticPro UT12/16/24 Scanner*

When I run **sane-find-scanner** it finds it sees the scanner too...
     *found USB scanner (vendor=0x07b3 [Plustek Inc.], product=0x0017 [USB SCANNER], chip=LM9832/3) at libusb:001:010*

However, when I try running **scanimage -L**  it doesn't detect the scanner.

I've tried all of this both as a normal user and as root and gotten the exact same results.

This is as much as I'm able to figure out on my own without any help. 
Any assistance in resolving this would be appreciated.

---

### Post by adyeths on 2007-04-15
Nevermind, I managed to figure out how to get my scanner working again on my own without anyone's assistance.

---

### Post by mp035 on 2008-02-11
Hi adyeths,
I am having the same trouble, my scanner used to work, and then just stopped, same symptoms as you.  Any hints?  Thanks.

---

### Post by adyeths on 2008-02-11
> **mp035 said:**
> Hi adyeths,
I am having the same trouble, my scanner used to work, and then just stopped, same symptoms as you.  Any hints?  Thanks.

The problem I had was related to usb suspend in feisty. There is a long thread about it here --> [https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488")

The fixes that were identified in that thread sortof worked, sortof didn't. They worked well enough for me for the few months that I used feisty. Upgrading to gutsy fixed the problems I was having completely. I haven't had any problems in gutsy.

---

