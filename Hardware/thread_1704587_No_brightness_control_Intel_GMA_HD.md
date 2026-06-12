---
title: "No brightness control Intel GMA HD"
date: 2011-03-10
forum: Hardware
---

### Post by darkangelous6 on 2011-03-10
Hi guys,

I have a Gateway Laptop ID49C07u that comes with Intel GMA HD, im running 10.10, everything works great except the brightness control, when i press the fn key combo it shows the gnome little app, and the brithness bar goes up and down, but the actual brightness level on the screen stays at 100%, im going blind here, not to mention the battery life issues. I have tried editing the grub file in /etc/default, and xbacklight with no good results. Any sugestions?

---

### Post by NightwishFan on 2011-03-10
This might not work but try booting with acpi_backlight=vendor. Adding boot options isnt hard but its a bit clunky to walk through. Do you know how?

---

### Post by darkangelous6 on 2011-03-10
I added this with no good results, it actually got worse since i couldnt even see the brightness gnome app:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor intel_idle.max_cstate=0"

---

### Post by NightwishFan on 2011-03-10
Ah, that works for some intel chips, not yours I guess. :D

---

### Post by darkangelous6 on 2011-03-10
Any other suggestions?

---

### Post by darkangelous6 on 2011-03-18
Help? \D:/

---

### Post by NightwishFan on 2011-03-18
At this moment I am unaware of anything that will fix it. Try a live CD (dont install, just run from the cd) of the latest Ubuntu alpha and see if your issue is fixed.
[http://cdimage.ubuntu.com/releases/natty/alpha-3/](http://cdimage.ubuntu.com/releases/natty/alpha-3/)

---

### Post by darkangelous6 on 2011-04-08
I dont know what else to try? Anyone??

---

### Post by fishbulb1022 on 2011-07-31
There is a ppa for a modified kernel that fixes this issue on laptops that use i915 graphics. I have installed the new kernel on my Acer Aspire 7740 and it works great. Hopefully the fix will be integrated into the main kernel soon. For now, here is the link the page where you can read about the modded kernel and the info for the ppa:

[https://launchpad.net/~kamalmostafa/...l-mjgbacklight](https://launchpad.net/~kamalmostafa/...l-mjgbacklight)

---

### Post by darkangelous6 on 2011-07-31
Page not found D:

---

### Post by Toz on 2011-07-31
Try: [https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight]("https://launchpad.net/~kamalmostafa/+archive/linux-kamal-mjgbacklight")

---

### Post by fishbulb1022 on 2011-08-02
Sorry about that, darkangelous, I copied the link from one of my old posts and assumed it still worked. The link Toz posted appears to be working though, and takes you to the page I was attempting to get you to. In case there are any issues or you don't feel like going to the page, the information is pasted below. Note that it will only work if you are using gnome (or unity) and have intel i915 graphics drivers. 


Adding this PPA to your system

You can update your system with unsupported packages from this untrusted PPA by adding ppa:kamalmostafa/linux-kamal-mjgbacklight to your system's Software Sources. (Read about installing)
Technical details about this PPA

This PPA can be added to your system manually by copying the lines below and adding them to your system's software sources.
Display sources.list entries for:

deb [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu) YOUR_UBUNTU_VERSION_HERE main 
deb-src [http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu](http://ppa.launchpad.net/kamalmostafa/linux-kamal-mjgbacklight/ubuntu) YOUR_UBUNTU_VERSION_HERE main 

Signing key:
    1024R/F37F3AB0 (What is this?) 
Fingerprint:
    77C69C59057A766866EE16C7E0319082F37F3AB0

---

### Post by darkangelous6 on 2011-08-06
Yeei that worked! Thank you so much! =D

---

