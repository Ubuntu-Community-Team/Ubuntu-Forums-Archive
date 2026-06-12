---
title: "TouchPad working, PS/2 mouse not working"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by namd3r on 2007-06-02
I installed Ubuntu 7.04 yesterday on a Compaq Presario 1200 laptop.  The touchpad is working great, but I have a Labtec PS/2 mouse connected that is not working at all.  The sensor is glowing, so I know it is getting power, but other than that, it doesn't do anything.  How can I fix this?

---

### Post by Jeanpaul145 on 2007-06-02
Maybe this will help:
I vaguely remember something about Xorg not being able to use 2 mouses at once (I read this while I was trying to determine whether the Logitech DiNovo Edge keyboard was a good buy while using Linux). Maybe (I'm not sure here!) that's the problem. If it is, you'll have to deactivate the touchpad when you're going to use your mouse.

---

### Post by namd3r on 2007-06-02
Alright, well, I'm new at the whole Linux thing, so could you tell me how I would go about deactivating my touchpad?

---

### Post by Jeanpaul145 on 2007-06-02
If you don't already have GSynpatics (for Gnome) or KSynaptics (for KDE) installed, you'll want to try that.
Just use the Synaptic Package Manager (confusing, isn't it?;)) and search for either one of them.
If You're gonna go with GSynaptics, you'll also have to follow some instructions located at
[http://http://gsynaptics.sourceforge.jp/]("http://http://gsynaptics.sourceforge.jp/").
Additionally, I would recommend backing up the files you're (unavoidably) gonna have to edit in advance.

Personally I have experience with neither, as I don't own a touchpad (or anything making use of one), but if I'm right, you SHOULD be able to use either one to configure (and disable) your touchpad.

If I'm wrong, you'll have the backups, and the uninstalling of the packages are a few clicks (no pun intended) away.

HTH!

---

### Post by namd3r on 2007-06-02
It didn't work.  As soon as I disabled the touchpad, nothing would work.  I found a usb mouse that worked perfectly as soon as I plugged it in, so I guess I'm going to go with usb and just forget about trying to get the PS/2 one to work.

---

