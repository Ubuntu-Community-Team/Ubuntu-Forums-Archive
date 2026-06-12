---
title: "Random Hang - Laptop - Logs?"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by cwolf on 2007-11-13
Hello,

I have an Averatec 1020 laptop which was flying with Feisty quite well, but seems to have gotten indigestion with an upgrade to Gutsy.

Lately, when I leave my laptop on AC power overnight or when I leave home for many hours, I come back to find that the laptop is in 'hang' state.

The screen is still lit, but is blank, and one of the indicator LEDs on the machine (looks like a lock or something) flashes repeatedly.

What logs can I check to find out what might be causing this?  I have tried /var/log/dmesg, /var/log/syslog, /var/log/kern.log, and so on, but I can't find any failures or serious errors.

It should be noted that the biggest struggles I've had with Gutsy have been with ndiswrapper, WPA, NetworkManager, and suspend/hibernate functionality.

Thanks for you help.

---

### Post by rummage_bin on 2007-11-13
I have no suggestions but a very similar problem with an HP dv6500z laptop (AMD turion dual core 64 with nvidia 7150 graphics/chipset running 32 bit version of 7.10.)  

The computer screen will freeze up, including the cursor, and the caps_lock light will start blinking on and off.  Moving the mouse or typing something has no effect (the cursor stays frozen, the caps_lock continues to blink).  

This will happen at random times, sometimes when the laptop is just sitting there unattended, and it always requires a power cycle to unfreeze.  

Have no idea which logs I should be checking but next time this happens I'll try pinging the laptop from another computer, if it doesn't respond I guess I'll just go back to 7.4. 

 I should mention that aside from loading the proprietary nvidia driver and tweaking xorg.conf everything appeared to be working fine out of the box.

---

### Post by cwolf on 2007-11-15
Thanks for sharing.  I think I will also go back to Feisty...  I thought upgrading to Gutsy would be beneficial to my computer, but so far, it has only been beneficial to my patience... :)

---

