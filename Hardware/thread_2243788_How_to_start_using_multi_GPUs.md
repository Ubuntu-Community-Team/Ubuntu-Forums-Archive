---
title: "How to start using multi GPUs?"
date: 2014-09-11
forum: Hardware
---

### Post by aapo4 on 2014-09-11
(x)ubuntu 14.04
Currently I have GPU-card with two outputs and two monitors connected. This works out-of-the-box.

Now I try to connect one GPU more and goal is to get three monitors working. How I should proceed?

I already tried:
A)
I attached second GPU and connected third monitor. Boot messages are visible only in that new monitor, also login screen (lightdm) and then Xorg. Two other monitors are blank all the time. xrandr doesn't show them.

B)
I tried with an another GPU. New monitor shows boot messages. When X starts every three monitors show Xubuntu's boot-animation, then old monitors get stuck and login screen is only in new monitor.

xrandr shows:
VGA-0 connected
S-video disconnect
DP-1-1 disconnected
DP-1-2 disconnected
(this new GPU has vga and tv-out)

I guess my cases A and B have different problem. So what to try next? Should this work out-of-the-box? Have I just encountered bug(s) which I could report or is this known missing feature? Is it relevant what cards, drivers and monitors I'm using (if I have tested them alone that they are working)?

---

### Post by aapo4 on 2014-09-19
I got something working.
I put two different GPU's, but both manufactured by nvidia. 

1) I installed nvidia-304 from repository. Note: nvidia-settings-304 on repository is pointing to the nvidia-settings-331 which is not working with this older driver. I installed working nvidia-settings-304 from Ubuntu 13.10 (by downloading deb).

2) I removed xserver-xorg-video-nouveau

3) Booted grub recovery, started root shell (mounted disk rw). Run 'X -configure', copied just created file xorg.conf.new to the /etc/X11/xorg.conf. Rebooted.

4) Every monitor is working. With nvidia-settings I tuned layout and created new xorg.conf. After boot layout works, but nvidia-settings can't show the correct layout (some monitors are above others and they works as expected, but nvidia-settings just show them on next to each others).

Monitors are paired: mouse cursor is moving seamlessly over any monitors, but window can be moved only across paired monitors. In xorg.conf they are 'screens'. I can start applications to selected 'screen' using 'DISPLAY=:0.1 xterm'. Not sure is this issue or not, but I don't have any idea how to merge different GPU's in the same 'screen'.

---

