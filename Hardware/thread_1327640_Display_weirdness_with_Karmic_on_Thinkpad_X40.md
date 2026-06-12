---
title: "Display weirdness with Karmic on Thinkpad X40"
date: 2009-11-15
forum: Hardware
---

### Post by taiji_jian on 2009-11-15
Hi guys,

I needs some help tracking down this strange behaviour that I'm about to describe. 

The first symptom of weirdness that I noticed is that when I initially log in, my pointer is invisible. I can see the default white pointer at the login screen, but as soon as I log into my account it disappears. It is still THERE... I can open menus, high light entries, and so on, I just can't see the arrow. Hitting Fn+F3 to lock the screen causes the pointer to reappear. 

Playing a video in TOTEM and switching it to full-screen mode also causes the pointer to re-appear.

The second symptom of weirdness that I noticed is that if TOTEM is playing a video (either in windowed mode OR full-screen mode), docking or undocking the X40 from its ultrabase causes the screen to go blank. The machine is not locked up - you can hear the video continue to play in the background, and I can connect to the X40 via ssh to reboot it - but I can't switch to a vterm rest it with ctrl-alt-del or anything. 

This only seems to happen when a video is playing. However, while experimenting with this, I noticed that docking/undocking the X40 with the ultrabase sometimes causes the mouse to disappear just like when I initially log in. 

I further noticed that whenever I dock/undock, the scren blinks off and back on. When it blinks back on, this is when the pointer disappears (or when it locks up if TOTEM is running). Some times, but not every time, at this point a little notification bubble will pop up saying "Could not configure monitor" and then it gives a code and a number, like "CT 57." 

I further FINALLY noticed that whenever I hit Fn+F7 (this is the combo to switch to the VGA output for an external display) I get EXACTLY the same behaviour as when I dock/undock with the ultrabase - screen blink, mouse disappearance, hang during TOTEM playback, occasional "could not configure monitor" message.

My understanding is that Fn+F7 issues an ACPI event, which is handled by a script some place. I'm guessing that that event/script is also happening whenever the X40 is docked/undocked with the ultrabase. I don't think this should be happening - this is new behaviour in Karmic.

But at this point I don't know where to look next. I would like to know, first of all, what script is being called; then second what that script is doing that causes my pointer to disappear and TOTEM to lock up. Finally, I'd like to know where I might find additional information about this; I've been through the system logs, including Xorg.0.log, and everything looks normal to me. But, I am not a guru.

---

### Post by taiji_jian on 2009-11-15
Here is my bug report related to this issue:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/475665](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/475665)

---

