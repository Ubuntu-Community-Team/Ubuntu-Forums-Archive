---
title: "Ubuntu 12.04 Black screen HP Envy 6t-1000"
date: 2012-08-29
forum: Hardware
---

### Post by Sagesparten007 on 2012-08-29
I recently bought a HP Envy 6t-1000 and am having trouble installing and getting Ubuntu 12.04 to work properly on this Ultrabook.

When I boot up to install Ubuntu 12.04 it will post all the text to the screen and then the screen will go black once the GUI starts up. To get past this I hook my ultrabook up via HDMI to a monitor and I can then go about installing Ubuntu. Once installed I can use "nomodeset" in the kernel line to get past the black screen and get into my desktop environment with it being displayed on my ultrabook screen. 

I am not sure whether this is a kernel problem or a graphics driver issue or perhaps a little of both. Anyone know what to try to remove the need of using "nomodeset"?

The HP Envy 6t-1000 is using Intel HD Graphics 4000
lspci | grep VGA shows Intel Corporation Ivy Bridge Graphics Controller (rev 09)

Thank you.

EDIT: It seems a lot of people are having issues with the HP Envy line of ultrabooks and getting black screens on boot. I am not sure if the fix that I found is universal for all Envy's but it is definitely an odd issue. It seems there was no need for using "nomodeset" or any other kernel option to get the graphics to work because the graphics were working perfect in the first place. The issue was that after Ubuntu would boot to the log in screen or any GUI the screen brightness was set to 0 and all I have to do is hit fn + f3 a few times to bring the brightness up on the laptop and behold, there is the log on screen. It's a very odd issue that I mistakenly discovered the fix for. Unfortunately you need to turn up the brightness every time the ultrabook restarts unless someone knew a way to modify the default boot brightness. I hope this helps someone out there having the same issue I had.

---

### Post by Luxor125 on 2012-08-29
I have the same ultrabook and I recently installed Ubuntu 12.04.
I was able to get the brightness working automatically at boot by editing the file /etc/rc.local adding the following line  

echo 5 > /sys/class/backlight/acpi_video0/brightness 

before exit 0:
Hope it works.

EDIT: instead of 5 you could have 10 for maximum brightness.

---

### Post by Sagesparten007 on 2012-09-08
> **Luxor125 said:**
> I have the same ultrabook and I recently installed Ubuntu 12.04.
I was able to get the brightness working automatically at boot by editing the file /etc/rc.local adding the following line  

echo 5 > /sys/class/backlight/acpi_video0/brightness 

before exit 0:
Hope it works.

EDIT: instead of 5 you could have 10 for maximum brightness.

Thank you! Works perfectly! Couldn't find the solution anywhere, thank you for replying to me. What an odd bug.

---

