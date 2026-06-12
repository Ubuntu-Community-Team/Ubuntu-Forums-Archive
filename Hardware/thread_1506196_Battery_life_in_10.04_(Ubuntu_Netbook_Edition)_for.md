---
title: "Battery life in 10.04 (Ubuntu Netbook Edition) for Asus EEE PC"
date: 2010-06-10
forum: Hardware
---

### Post by adam988 on 2010-06-10
Hi,

I have an ASUS EEE PC 1005PE running UNE 10.04. In windows 7 i have  a battery life of roughly 10-11 hours while working but using Ubuntu this drops to 6 hours tops. Any tips?

Thanks

---

### Post by a__l__a__n on 2010-08-12
Have you tried the CPU Frequency Scaling applet?  Just add it to the gnome panel and choose a lower cpu frequency.  That can save a significant amount of power.

Also, try dimming your display "manually" with the Fn-key (Fn-F5 on my Asus eee 1000he if I remember right).

And the powertop utility can be helpful to identify what is using power.  

  sudo apt-get install powertop

Just run "powertop" at a command prompt.  It will show you what is using power and will suggest settings changes etc to reduce power.

Editing to add...  Netbook Edition doesn't let you add applets to the panel.  There are ways around that... but easier still, do it from the command line:

cpufreq-selector -g ondemand

or 

cpufreq-selector -g powersave

Or after boot, run

sudo /etc/init.d/ondemand start

---

### Post by adam988 on 2010-08-16
I have done all of those things but it still seems to be very short..any other suggestions?

---

