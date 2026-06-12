---
title: "Clickpad Problems - Asus A55A with Ubuntu 12.04"
date: 2014-03-06
forum: Hardware
---

### Post by joe-niezelski on 2014-03-06
Hello,

I'm new to Linux, but recently installed Mint on an Asus A55A after the HDD died, resulting in a lost Windows key. I ran into the below problem while using Mint, so I tried replacing it with Ubuntu, but the problem still occurs.

Basically, the clickpad (it's a touchpad with no discrete physical buttons) isn't working correctly. Some examples:

1) If I rest my finger on the button area, the pointer can't be moved with another finger. If dual-touch scrolling is enabled in the touchpad settings, moving one finger while having the other resting in the button area will cause the window to scroll. If it's disabled, the pointer will just freeze. 
2) Right-clicking while a finger rests on the touchpad acts as a left-click. 
3)The sensitivity slider in the touchpad preferences doesn't seem to have any effect.

I followed the instructions for creating and editing /etc/X11/xorg.conf.d/50-synaptics.conf, but that just allowed me to manually change the pointer speed, touchpad borders, etc. I tried to just make the button area "dead" to touch by adjusting its area, but although it prevented it from being used to move the pointer, resting a finger there still caused the issues above.

The only fix that kind of worked was creating and editing psmouse.conf. This prevents the "resting finger freezes pointer" issue, but also prevented me from disabling tap-to-click and enabling dual-finger scrolling. It also slows down the pointer's movement. I can't find any way of changing these behaviors.

I've been researching the issue for the past couple of days, without much luck. In fact, it seems like this problem has existed since at least 2010. Like I said, I'm completely new to Linux, so at least this gave me some practice with the shell, but this is my girlfriend's computer, and she would really like it to be working correctly (that is, the clickpad's behavior should be comparable to how it was in Windows). It's starting to get difficult to make a convincing case for Linux, but I'm hoping someone can help me save the day.

To clarify, here's what she finds necessary to be comfortable with the clickpad: she should be able to rest a finger on the button area while still moving the pointer, she should be able to disable tap-to-click, and she should be able to adjust the pointer speed.

Thanks in advance for any help you can offer.

---

### Post by phidia on 2014-03-07
[This Ubuntu guide]("https://help.ubuntu.com/community/SynapticsTouchpad") might help. Specifically review and use the > Control touchpad features using synclient section to adjust your trackpad-use the earlier sections if you need to ID the track pad. Hope that helps.

---

