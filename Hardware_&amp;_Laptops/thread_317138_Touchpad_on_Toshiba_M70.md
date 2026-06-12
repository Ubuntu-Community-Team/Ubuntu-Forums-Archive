---
title: "Touchpad on Toshiba M70"
date: 2006-12-11
forum: Hardware &amp; Laptops
---

### Post by nomadique on 2006-12-11
I have weird problem. Just installed Ubuntu and found that basically touch pad works but it doesnt allow scrolling on the side of the touchpad, instead it is minimizing all the windows all the time so it is really hard to work with it. Also funny thing is, to try and fix the issue i tried to login as root. When i login the touchpad freezes without any chance to get normal. fn +F9 doesnt help. I got back to the normal user account and mouse was frozen there initially as well. Then it recovered and somehow it stopped minimizing windows and allowed me to scroll on side of the touchpad. I really wanted it to stay this way, but after restart it got back to normal. repeating the steps helped again. Can someone please post how to set it forever like this, and also how to use mouse in root. Thanks in advance. Paul

---

### Post by TubaTodd on 2006-12-12
This may be part of the ongoing "Alps/Synaptics" issue which is a major annoyance. I have tried a TON of different advice, but I could not fix the issue.

First of all, under Dapper my touchpad on my Toshiba works GREAT. Under Edgy, the touchpad is NOT detected on initial bootup. I must hit ctrl+alt+backspace and restart x in order for it to be detected properly. 

If Edgy didn't work for you, you might try Dapper.

---

### Post by nomadique on 2006-12-13
Ghm, to try Dapper do i have to uninstall this Ubuntu download new release and install it from scratch loosing all the work?

---

### Post by stenka on 2006-12-14
Check this :
[https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68540](https://bugs.launchpad.net/distros/ubuntu/+source/xserver-xorg-input-synaptics/+bug/68540)

You can switch to a virtual terminal and come back to get your touchpad working :
[CTRL]-[ALT]-[F1] and then [CTRL]-[ALT]-[F7]

---

### Post by nomadique on 2006-12-17
Thanks for responce i looked at the suggestions there. Copied nececery information to my xorg.conf but it didnt work. I wonder if info from my xorg is being read by the mashine. Because the scroling option didn;t change and i have set SHMconfig "true" in xorg but gsynaptics still gives me an error saying that i have to set SHMconfig true option to run it. What can it be? Edgy sucks ;(

---

