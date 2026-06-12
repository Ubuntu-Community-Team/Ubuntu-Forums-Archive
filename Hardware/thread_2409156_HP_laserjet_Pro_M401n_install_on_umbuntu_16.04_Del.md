---
title: "HP laserjet Pro M401n install on umbuntu 16.04 Dell"
date: 2018-12-28
forum: Hardware
---

### Post by lawrence_hickey on 2018-12-28
My new Dell 7530 needs to be hooked up to my HP Laserjet Pro M401n.  (printer works on old linux mint 13 model) usb ports all seem find on the 7530,
installed HPLTP-3.16.3.  went ok for a while but got to the HP Device Manager Setup screen and it can't find my USB.  did lsusb and even gave it the exact bus:device address. did not help.
I can get to this screen now any time i want running hp-setup. ahd the HP device manger screen comes up- the one that can't find my USB. Tried other USB which i know work, - no cigar.
I run lsusb and can see that this is plugged into my HP printer. so all looks sane from the linux side I think. but the HP device manager cant find it.

---

### Post by Enigma12 on 2018-12-30
For my Lubuntu 16.04, I needed to install CUPS to get my HP Laser printer to install and work. Been a while since I did that, so I hope I give you correct process. I will find out very soon if Lubuntu 18.04 does the same. 

Try in Terminal "sudo apt install cups" w/o the quotes. If you've never done that, note that when you type in your password, nothing happens on screen. That's normal. Just press Enter after you enter your password. After CUPS loads, try again installing the printer. In case it's not obvious, the printer must be turned ON and, as far as I know, at the Ready state for the configuration to happen.

I did NOT install HPLIP, but the printer works perfectly. 

Hope this helps. If not, maybe someone will offer better advice.

---

