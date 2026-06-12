---
title: "Pc not booting while HDMI connected"
date: 2019-09-13
forum: Hardware
---

### Post by burnout2000 on 2019-09-13
Hi,

I have a Minix N24C-4 mini PC with installed Ubuntu 18.04.01.
In general the PC with Linux is working fine with a connected monitor with 1920x1080 resolution. 
No I'm trying to get another Monitor running with 1888x1728 resolution. I have set the timings in the xorg.conf, since the resolution via EDID isn't set properly in Lniux.
If I boot the PC with the standard FullHD monitor, disconnect the FullHD monitor after booting and connect the other one with 1888x1728, everything is working fine.
But if I boot the PC with connected 1888x1728 monitor nothing happens. The PC stuck somewhere during boot. 
The only solution that I ahave at the moment is, disconnect HDMI, wait until NUM lock is turned at the keyboard and than connect HDMI. This is my current workaround. 
What is going wrong here?

Appreciate all comments / hints / solutions

Thank you

---

### Post by ryansenn on 2019-09-13
Do you get stuck on this image or is it completely blank? [https://www.reddit.com/r/Ubuntu/comments/c2xkaw/ubuntu_1904_doesnt_start_if_my_hdmi_cable_is/](https://www.reddit.com/r/Ubuntu/comments/c2xkaw/ubuntu_1904_doesnt_start_if_my_hdmi_cable_is/)

---

### Post by burnout2000 on 2019-09-13
it is completely blank. Nothing visible

---

### Post by burnout2000 on 2019-09-13
in addition:
I've done another test:
Using a notebook and a live linux USB drive. 
While HMDI to the 1888x1728 display is connected with the notebook, there is during boot a repeating message: "nouveau .. DRM: core notifier timeout"
HDMI removed, live linux boot successfully

---

### Post by hk42 on 2019-09-25
Hi
I had the same problem on an ARM device running OpenElec.
The "solution" I found is to switch off the TV while booting.
When you switch off a modern TV you have to wait some time until it is really off
like a computer.
HDMI connectors are not designed for frequent use here all was done with the remotes.
No mechanical stress of any kind.
When booting with the black screen Linux was live and could be talked to via SSH.
HDMI sound was OK too so this could be DRM related.

---

