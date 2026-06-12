---
title: "Resolution Problem"
date: 2010-10-26
forum: Hardware
---

### Post by Minovate on 2010-10-26
I'm completely new to Linux and Ubuntu, I've installed 10.04 (Lucid Lynx) and my display was stuck at 800x600 and I couldn't change it, when I was going to search for a monitor it comes up with Monitor:Unknown. I upgraded to, 10.10 (Maverick Meerkat) and yet the same problems still occur. Would anyone be so kind as to help me get through this? I've heard a lot about Ubuntu and I want to try it out.

My Screen Resolution is : 1366x768.
My Laptops Graphics card is : NVIDIA GEFORCE GT 420M
My Laptop is an Acer Aspire 4741G

---

### Post by irv on 2010-10-26
It sounds like you do not have the right driver. Try this: 
System> Administration> Additional Drivers. It will search your system and see if you need additional drivers and will give you the option to load them. When the list appears just chose the one for your video card. Hopefully this will fix your problem.

---

### Post by odzk on 2010-10-26
just follow what IRV said, once you have it installed, you said see the nvdia icon, from there you can change the resolution.

---

### Post by Minovate on 2010-10-29
When i install the driver, it says i needa reboot for it to work, but once i reboot the computer ubuntu won't load up :/

---

### Post by ipey on 2010-10-29
Hope this will help you.
I found this:
> 
DO NOT INSTALL THE RESTRICTED NVIDIA  DRIVER. Doing so will enable the Nvidia chipset which will cause the  screen to turn off when you enter Gnome. To get the Nvidia chip working  you would need to figure out how to install/use vga_switcheroo. from this: [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

edit: the warning is actually for an ASUS netbook, but there might be a relevant solution

---

### Post by Minovate on 2010-10-30
@ipey i don't get what u mean o.o

---

### Post by ipey on 2010-10-30
well, the documentation tells that you cannot install nvidia driver directly. There are some steps you have to complete first (I'm competent enough to elaborate this). I didn't find howto for your netbook there though but maybe visiting the page will lead you to solution. good luck.

---

