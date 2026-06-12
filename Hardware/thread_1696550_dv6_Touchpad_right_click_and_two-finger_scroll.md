---
title: "dv6 Touchpad right click and two-finger scroll"
date: 2011-02-27
forum: Hardware
---

### Post by quasitonality on 2011-02-27
I just got a new HP dv6 notebook and installed ubuntu 10.10 on it. The touchpad worked out of the box, as far as tracking, tapping, clicking, and edge scrolling. But the right click button doesn't work, and the two-finger scrolling doesn't work. The computer came with Windows 7, and the two-finger and right click both work on that operating system.

I read through some forum posts that seemed to deal with similar two-finger scroll issues, and I followed the instructions I found, but it didn't seem to work. After updating with aptitude safe-upgrade, I used xinput to change these settings:

xinput set-int-prop 11 "Two-Finger Scrolling" 8 1
xinput set-int-prop 11 "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop 11 "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop 11 "Synaptics Two-Finger Width" 32 8

I used xinput list-props to confirm that the changes had indeed been made, but the two-finger scrolling still didn't work. Just as a test, I used xinput to turn edge-scrolling off and on, and those changes took effect immediately. Any suggestions as to what else I can try?

---

### Post by Slave2Metal on 2011-02-27
Have tried  [https://bugs.launchpad.net/ubuntu/+s..._1.1.1_all.deb]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/308191/+attachment/1771346/+files/synaptics-dkms_1.1.1_all.deb")

then 
```
sudo dpkg -i synaptics-dkms_1.1.1_all.deb
```

---

