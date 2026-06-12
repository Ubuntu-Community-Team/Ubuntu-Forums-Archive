---
title: "NOOB Needs Display Help"
date: 2008-06-17
forum: Hardware
---

### Post by pwhitted on 2008-06-17
Greetings!

This is my first foray into the Linux world. I've installed Hardy on an HP zd7010 Pavilion laptop. I've had the display properly configured with the nVidia-glx driver and achieved 1440x900 resolution. Foolishly, I followed steps in another thread and installed nvidia-glx-new. After rebooting, the system came back up with 640x480 resolution. I THINK I've managed to uninstall that driver (sudo aptitude remove nvidia-glx-new?), and reinstall the nvidia-glx driver (sudo apt-get install nvidia-glx), but still can't get any better than 800x600 resolution. How do I get this back to the better resolution? I've searched these forums, but not had much luck. Many of the threads I've found were written at a level that is way beyond my skill level. TIA! - Pat

---

### Post by phidia on 2008-06-17
Is that a 17" screen with that rez? (Just wondering)
In Hardy you should be able to enable the nvidia card by using the
System>Hardware Drivers menu. If that doesn't get the best driver working try looking at the [guide here]("https://help.ubuntu.com/community/XORGHardy"). 
Hope that helps.

---

### Post by Daedal Dementia on 2008-06-17
thats what i did. it worked for me

---

### Post by NullHead on 2008-06-17
I'd probably try```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then ```
sudo /etc/init.d/gdm restart
```Note the last command will restart the xserver just as if you were to restart the computer; will loose all current documents or web pages open atm.

---

### Post by pwhitted on 2008-06-17
I thought the same thing, Phidia. Oddly enough, when I enable the nvidia 3rd party driver via the Hardware Drivers menu, I get lower resolution than without it. I'll try checking out the guide you recommend, or NullHead's suggestion. Thanks! - Pat

---

### Post by pwhitted on 2008-06-17
NullHead's suggestion was just the ticket. Thanks! - Pat

---

### Post by cantseejack on 2008-06-24
> **NullHead said:**
> I'd probably try```
sudo dpkg-reconfigure -phigh xserver-xorg
```Then ```
sudo /etc/init.d/gdm restart
```Note the last command will restart the xserver just as if you were to restart the computer; will loose all current documents or web pages open atm.

Another nub here. I was having some problem with my girlfriend's Thinkpad T61 display (wrong resolution, refresh, etc.; Nvidia Geforce 8 was detected, but that's not the computer spec) and I ran those commands and it seemed to fix whatever was wrong. What does that do?

---

### Post by NullHead on 2008-06-25
> **cantseejack said:**
> Another nub here. I was having some problem with my girlfriend's Thinkpad T61 display (wrong resolution, refresh, etc.; Nvidia Geforce 8 was detected, but that's not the computer spec) and I ran those commands and it seemed to fix whatever was wrong. What does that do?

I guess I should've explained what they do before I go having someone blindly running them ... 

What the first command does is: reset the configuration file back to its defaults and rescan your hardware. If there is any changes to your hardware, it'll automatically detect them and try its best to put in the best settings it can. 

The second command restarts the whole [GUI]("http://en.wikipedia.org/wiki/GUI") so the effects of the first command are taken into effect with out the need to restart the computer.

---

