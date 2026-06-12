---
title: "Synaptics Touchpad Jitter"
date: 2011-02-14
forum: Hardware
---

### Post by win_expat on 2011-02-14
Hello Linux goers, I just recently installed Ubuntu 10.10 onto my Acer 6920G on a second partition beside Win7 because I need it for a class. So far it's lovely and has been easier than I thought; the only trouble I had was getting sound through the hdmi cable, and now the cursor shake. 

The cursor will shake or jitter when holding my finger down on the touchpad without moving it; it seems to be overly sensitive. I searched the internet all of yesterday, and found some hacks, but nothing that worked well. I tried gpointing-device-settings, but that didn't seem to work, or at least the settings wouldn't remain after a reboot. I also tried "sudo modprobe -r psmouse" "sudo modprobe psmouse proto=imps", which removed the shake, but make the touchpad too slow and without scrolling. It also occurs in openSuse, but not Win7.

I'm wondering if anyone knows a solution for this. It's not extremely important, I can just buy a wireless mouse, but figured I'd ask.

Thanks

---

### Post by win_expat on 2011-02-15
Actually found solution that worked: [http://ubuntuforums.org/showthread.php?t=168581&page=3](http://ubuntuforums.org/showthread.php?t=168581&page=3)

I uninstalled gpointing-device-settings and then added Heinzelotto's code to /etc/X11/xorg.conf. Just needed to tweak the MinSpeed and MaxSpeed and now the cursor isn't shaking!

---

