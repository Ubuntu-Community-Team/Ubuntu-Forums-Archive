---
title: "CPU Frequency scaling while overclocked"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by Linder on 2008-04-10
Hi there! 

I've checked related posts about this issue, but not been able to find anything conclusive. First off, my specs:

Intel Core 2 Duo E6600 (2,4 GHz x 2)
Asus P5B-E Motherboard
2x1024Mb Kingston HyperX PC6400
ASUS Nvidia GeForce 8800 GTS 320 Mb
Running the above on Ubuntu Hardy Heron (8.04 BETA) x64 bit.

So, that's my setup. Using different tools (and some Windows stresstesting) I've overclocked my processor cores to 3.22 GHz instead of the standard 2.4 GHz. This is all good and well, except that Ubuntu was hellbent on turning my frequency back down to 1,6/2,4 (which is the frequency scaling). It will idle at 1.6 GHz and when something requires attention, it'll switch up to 2.4 GHz. That's good and will save both power and heat. However, since I have overclocked memory, graphic card and processor, it's a bit annoying that Ubuntu will set itself above me and refuse me my 3.22 GHz.

So, I did some looking around and found_ [this thread]("http://ubuntuforums.org/showthread.php?t=248867")_ on the subject. I followed it to point except that I forgot to put in the acpi-cpufreq module in the /etc/modules file which essentially killed any CPU frequency scaling in Ubuntu at all. The gnome-applet failed with an error message, but did still display my CPU frequency (but couldn't change it by speedstepping). To my surprise it did now display 3.22 GHz. It never budged either up or down and both my cores ran hotter than before, suggesting that it was actually running at the overclocked frequency and the computer was noticably faster.

So, happy I was that I succeeded I went to troubleshoot why I couldn't define powersaving governor and set the frequency myself. I found (eventually) that I had forgotten to put the acpi-cpufreq into /etc/modules. I did that and rebooted. Lo and behold! I still couldn't change the frequency. It was locked at ondemand. So I googled a bit and found the ```
sudo dpkg-reconfigure gnome-applets
``` which allowed my to actually change the governors and the frequency on the fly. I can now change the power schedule (conservative, powersave, performance and ondemand) and the frequency will alter accordingly. BUT! There's always a but...

The frequency is now back to switching between 1.6 GHz and 2.4 GHz as follows:

powersave = 1.6 GHz constantly
ondemand = 1.6 GHz idle, 2.4 GHz at any activity at all
conservative = 1.6 Ghz most of the time, 2.4 GHz during heavy load
performance = 2.4 GHz constantly.

That's the way I want it to work, but unfortunately I have no way to get my BIOS overclocked speed of 3.22 GHz without totally killing any speedstepping (that is, disable speedstepping completely by removing the acpi-cpufreq module).

Anyone have a solution for this? I seem to remember from windows that it was changing the CPU multiplier between 6 and 9 to set the stepping, and as such it was toggling between 

6x355 = 2130 (2.1 GHz) and 9x355 = 3195 (3.22 GHz).

It'd be a tad bit cumbersome to reboot every time I want to go between performance (3.22 GHz) mode and the more powersaving options availible thru the applet.

---

### Post by Linder on 2008-04-10
le bump

---

### Post by Linder on 2008-04-16
Anyone?

---

