---
title: "Is there a way to configure hothey-setup?"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by Sammi on 2006-08-04
Hotkey-setup is a little app that launched by default on Ubuntu and it is responsible for making special hotkeys work, like special volume and other media buttons.

My problem is that the volume button only changes the master channel, which doesn't behave correctly on my system(haven't been able to fix it), so it want it to change the volume of my PCM channel in stead, which in praksis works more like a master channel.

I found out that some special commands to amixer do what I want. Like this:
amixer sset PCM 1+ unmute
amixer sset PCM 1- unmute
amixer sset PCM mute

Is there a way to configure hotkey-setup to send these commands when I press the volume media keys and mute button?

---

### Post by patrick295767 on 2006-08-04
> **Sammi said:**
> Hotkey-setup is a little app that launched by default on Ubuntu and it is responsible for making special hotkeys work, like special volume and other media buttons.

My problem is that the volume button only changes the master channel, which doesn't behave correctly on my system(haven't been able to fix it), so it want it to change the volume of my PCM channel in stead, which in praksis works more like a master channel.

I found out that some special commands to amixer do what I want. Like this:
amixer sset PCM 1+ unmute
amixer sset PCM 1- unmute
amixer sset PCM mute

Is there a way to configure hotkey-setup to send these commands when I press the volume media keys and mute button?

In gnome-panel or kde, there is hotkeys normally ... If i recall well.  (depends your desktop)
 
For your multimedia keyboard : keytouch [http://keytouch.sourceforge.net/dl-keyboards.html](http://keytouch.sourceforge.net/dl-keyboards.html)

---

### Post by mikedoth on 2007-08-02
System -> Preferences -> Keyboard Shortcuts:)

---

