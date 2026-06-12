---
title: "Netbook issues with Ubuntu 12.04 LTS"
date: 2012-08-24
forum: Hardware
---

### Post by Spookas on 2012-08-24
I bought an Acer Aspire One 756 Series Netbook with the intention of using it on the go. I immediately installed Ubuntu 12.04 LTS on it, but am having two main problems.

1. My right-click doesn't work the way I'd like it to. I have to click in the bottom-right corner of the track pad (where the buttons are not separate) to right-click, and the area for that is very small and hard to find consistently.

2. I can't adjust the screen brightness at all. I've had it on for about 4.5 hours and it's just about to die, but I'd really like to increase the battery life by turning the brightness down; it is on as bright as it can be, and I can't turn it down.


I have used Linux for a while on my older laptop, but never came across this sort of issue, and I don't have a clue where to begin. 

I appreciate any help you can provide!

---

### Post by ahallubuntu on 2012-08-24
Brightness-control issues are very common in Linux with laptops.  Usually the solution involves setting something in  your Grub default file and updating Grub.

As described here:

[http://ubuntuforums.org/showthread.php?t=2041487](http://ubuntuforums.org/showthread.php?t=2041487)

---

### Post by saou on 2012-08-25
> **Spookas said:**
> My right-click doesn't work the way I'd like it to. I have to click in the bottom-right corner of the track pad (where the buttons are not separate) to right-click, and the area for that is very small and hard to find consistently.

I feel your pain about right-click; I've given up on it a few minutes after installing xubuntu 12.04.  My solution is to two-fingure-tap on the touchpad.  I  ap-get install gpointing-device-settings  and adjust the setting to suit my preference.  Right now I can two-finger-tap anywhere on the touchpad to subsitute for the right click.  NOTE:  (1) this is for xubuntu, but I'm sure something like this would work in ubuntu.  Do note that xubuntu's setting mananger does allow users to tweak the touchpad but gpointing-device-setting allows for extra tweaks.  (2)it's not 100%; usually a single two-finger tab within firefox will bring up the firefox right-click menu, but when the mouse is in the desktop often I have to double two-finger tap to bring up the desktop right-click menu (still better than fighting the lower-right-hand-corner click).

Good luck and let us know how it turns out!

---

### Post by Spookas on 2012-08-25
> **ahallubuntu said:**
> Brightness-control issues are very common in Linux with laptops.  Usually the solution involves setting something in  your Grub default file and updating Grub.

As described here:

[http://ubuntuforums.org/showthread.php?t=2041487](http://ubuntuforums.org/showthread.php?t=2041487)

Thanks! The instructions in the link worked perfectly for me!

As for the right-click... one of my friends told me to just try double-tapping with two fingers and see if it worked. It did, and it works good enough for me.

Thanks again for the help!

---

