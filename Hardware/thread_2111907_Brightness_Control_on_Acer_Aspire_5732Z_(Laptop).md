---
title: "Brightness Control on Acer Aspire 5732Z (Laptop)"
date: 2013-02-03
forum: Hardware
---

### Post by ksbd on 2013-02-03
First off, I'm new as of yesterday to Linux, so I'm lacking specific knowledge...

I installed Ubuntu 12.10 using an external monitor as the backlight was not working on the laptop.
Then, I installed mesa-utils which changed the graphics status from unknown to: Mobile Intel® GM45 Express Chipset x86/MMX/SSE2 
Still without a fix, I tried:
```
echo 65 | sudo tee /sys/class/backlight/intel_backlight/brightness                      
```which finally turned the laptops backlight on, though only each time I run it.
On the same post I found this code, it said to edit grub.cfg to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi_backlight=vendor                      
```which I did, but nothing changed after I updated grub  and rebooted.

I'm looking for a way to make the backlight always be on, rather than having to type the first set of code into the terminal every time, but I'm too much of a noob to know how to do this...
Any help?

Additional: My fn key doesn't work (hardware problem) so I can't control brightness this way.

-- Fix --

Follow this guide: [http://www.youtube.com/watch?v=0OE-Oez1NCw](http://www.youtube.com/watch?v=0OE-Oez1NCw)
replace "lampp" with whatever you decide to name the script, and replace the 2nd line (after using nano) with the first code mentioned in this post. Then reboot to check it worked.

---

### Post by Toz on 2013-02-03
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" acpi_backlight=vendor

acpi_backlight=vendor should be _inside_ the second quote, like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

You can always check which kernel parameters are in effect by running the following command:
```
cat /proc/cmdline
```

---

