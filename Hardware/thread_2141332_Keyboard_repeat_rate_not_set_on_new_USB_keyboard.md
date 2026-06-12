---
title: "Keyboard repeat rate not set on new USB keyboard"
date: 2013-05-02
forum: Hardware
---

### Post by chorca on 2013-05-02
Hey guys. Having an issue with 13.04 and a USB keyboard. Running on a Thinkpad X220. Using XFCE as a window manager.

I've set my repeat rate and delay to my personal values (faster repeat rate, slower delay), and these work fine, they come up every time, etc.

However, when I plug in a USB keyboard or dock the computer, the settings are not applied to the new keyboard. I can get them to work, but it requires going into the keyboard settings, nudging the slider on Repeat Rate OR Delay up or down a notch, at which time the settings are applied to the new USB keyboard. Super-annoying, at worst, but it's just one of those things.

This seems to have popped up some time ago, under this bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/427168](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/427168) , however, it has since been fixed by the Gnome team and closed. As far as i can tell, this is a regression. Anyone else have this issue? Know of a fix for it? Not sure if XFCE is using the same method to set the keyboard settings, since I'm not sure how much XFCE and Gnome share utilities to set this stuff. If so, curious if I should open a ticket to XFCE?

---

### Post by wirawan0 on 2013-06-26
I am having a similar issue, albeit using a different distro (Debian 7, xfce 4.8). I think you should file a bug report, since xfce setting tools are different from GNOME. If and when you file this, pls post the bug url here.

Edit: sorry, I found your bug report, here:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1180120](https://bugs.launchpad.net/ubuntu/+source/xfce4-settings/+bug/1180120)

Thanks for this.

---

