---
title: "Nvidia Geforce 7300 problem"
date: 2005-12-12
forum: Hardware &amp; Laptops
---

### Post by ses on 2005-12-12
Hi, I just setup Ubuntu 5.10 breezy (i386) on my Asus A6000Km laptop, it's specs:
AMD Turion MT-30
some SiS chipset (will look it up)
nvidia geforce 7300
it's got a 1280x800 screen

I've got the nvidia drivers setup and they seem to work fine until I try firing up X11. I get the error:

NVIDIA(0): failed to allocate rankine object

And no screens found.

The driver being used is 76.67

However when I use the open source "nv" driver my X11 works fine, it's just when I change it to "nvidia" instead of "nv", that everything goes to hell, the nvidia kernel module is loaded of course, and I saw the version number of the driver by looking at dmesg, where I can see the module loads without errors.

I'm also using Ubuntu breezy on my workstation, a Dell  optiplex gx620, where I've got a geforce 6600GT card, and my X11 works fine.

Anyone have any idea what this might be, should I try a different screen resolution perhaps?

Thanks,
Steinn

---

### Post by WildTangent on 2005-12-12
The 7300 is rather new is it not? Give it some time would be my best advice, and see if you can file a bug with nvidia.

-Wild

---

### Post by ses on 2005-12-13
Yes, perhaps this graphics card just isn't supported yet, at least I don't even find it on the list of supported GPUs in the 81.74 driver README .. I hope support for it will come soon :-/

---

### Post by ses on 2005-12-13
Just a minor update, if anyone else is having the same problem, I did some sniffing around and found out that Geforce Go 7300 is on the list of currently supported hardware for the 82.10 driver, although that one is not out for Linux yet, something from the 82.xx family should be available in the next couple of weeks I imagine! :D

---

### Post by ses on 2005-12-14
Just wanted to tell you that on the nvnews.net forums an nvidia employee told me that a Linux driver supporting (amongst others) the 7300 cards was expected in early 2006.

---

### Post by tseliot on 2005-12-14
By the way this is the list of the supported graphic chips:
[http://download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/appendix-a.html]("http://download.nvidia.com/XFree86/Linux-x86/1.0-8174/README/32bit_html/appendix-a.html")

---

### Post by flyingfrog on 2006-03-24
[QUOTE=ses]However when I use the open source "nv" driver my X11 works fine,[/QUOTE]

Mine not!! Damn... my "nv" driver doesn't work as espected! ](*,) 

Could you send me your working xorg.conf with "nv" drivers?

---

