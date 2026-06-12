---
title: "SiS 661FX - Enable/Disable CRT output"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by imbunche on 2006-02-03
Hi all, 

I know there are million threads on how to enable/disable external displays for various laptop models. I could not find anything for mine.

My laptop is an ECS  G557, as the subject says it has a SiS661FX graphics controller.

In general it works fine with Ubuntu. Hibernate suspend are a bit flaky but workable.
In order to connect an externl monitor the only way so far is to boot the laptop with the monitor connected.
Also I have not find a way to switch between LCD/CRT display, the advertised Fn hotkey (Fn+F12) does nothing.

Can someone help me please???

---

### Post by bernardfrancois on 2006-02-04
Often, a laptop will detect an external monitor during the boot process. If it doesn't detect any, it will disable the external video output.

If you want your laptop to skip that detection and enable the external video output anyway (also if you won't be using it, so then youre probably consuming more electricity than necessary), you might be able to set this in the BIOS setup.

If you want to be enabling/disabling this while your laptop is running, the driver for you video card will have to support this. Maybe you'll read more in the documentation of your driver (if it's possible to do this, and how to configure it).

---

### Post by imbunche on 2006-02-05
Hi, 
thanks a lot for your answer. From RTFM I got to the site os sis' drivers developer.
Great site, lots of info and the solution to my problem.

I donwloaded the sisctrl utitlity which allows you to do neat things to your screen without having to restart the Xserver.
I'll probably link 'sisctrl -siscrt2 "off" ' to my Fn+F12 key.

I'm even able to use and external VGA + my laptop screen thanks to the instructions on the site.

Thanks again and for sis related issues look at:
[http://www.winischhofer.net/](http://www.winischhofer.net/)

---

