---
title: "aspire 3820 touchpad trouble"
date: 2010-09-04
forum: Hardware
---

### Post by geefok on 2010-09-04
Hellow, guys!
Please help me with a little trouble. I have Acer aspire TimelineX 3820 TG laptop and ubuntu 10.04 installed on it. I have f trouble with my touchpab scroll bar (this is a line in the right side of touchpad, whitch must be like scroll on mouse), it works only to scroll down. If i lead finger down - it scroll down, if i lead finger up -it scroll down too. Do anyone have some ideas about it?
Best regards.

---

### Post by geefok on 2010-09-07
up

---

### Post by nille on 2010-09-07
Hello, geefok!

I do not have a solution for you, but I want to save you some trouble: apparently, Acer decided to change some of their hardware in the 3820TG-models. Most likely, they changed the long, bizarre additional numbers after the base model-number (you know, the ones that nobody cares about?). In my case they are: 3820TG-5454G32n, what is yours? As soon as I can talk to the owner of the other 3820TG, I will ask her what her exact model number is. Because on my computer, wlan worked out-of-the-box, while my touchpad had the same issues as you describe - and vice versa on the other computer.

I did not notice this at first, since I tried to install Archlinux on my computer instead of Ubuntu. But after trying to patch the Arch kernel with Ubuntu-specific patches for half-a-day I gave up and installed Ubuntu, just to realize it isn't even the same hardware!

Now, on to your problem: the problem seems to be that evdev/synaptics (or whatever) does not detect the touchpad as an actual touchpad-device. Instead, it just detects it as a "ImPS/2 Generic Wheel Mouse" (See: /proc/bus/input/devices).

However, on the other 3820TG it reports the touchpad as a "SynPS/2 Synaptics TouchPad" and the synaptics driver kicks in (xserver-xorg-input-synaptics), so apparently they've changed hardware.

Since I just realized this, I do not have had the time to search for any solution to this problem. But I will keep looking! Please, post in this thread if you find anything interesting..


**EDIT:** Update, found some bugs that might be related:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565543)

---

### Post by nille on 2010-09-07
I think I've found a solution in this post:
[http://www.backports.ubuntuforums.org/showpost.php?p=9306708&postcount=6](http://www.backports.ubuntuforums.org/showpost.php?p=9306708&postcount=6)

What you do, basically, is to add:
```
options psmouse proto=imps
```
to the file /etc/modprobe.d/psmouse.conf (create the file if it doesn't exist).

Good luck!

---

### Post by TimoteoLimon on 2010-12-26
I have problems creating the file in /etc/modprobe.d/ I think i need some sort of pivileges, but I have no idea how to get them.

---

### Post by Fashion on 2011-02-20
> **TimoteoLimon said:**
> I have problems creating the file in /etc/modprobe.d/ I think i need some sort of pivileges, but I have no idea how to get them.

Try write: "sudo gedit /etc/modprobe.d/psmouse.conf" without quotes in the terminal. Then enter your password.

---

