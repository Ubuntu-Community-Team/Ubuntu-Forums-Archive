---
title: "Will someone please explain what's up with xorg.conf??"
date: 2008-11-14
forum: General Help
---

### Post by tehfade on 2008-11-14
I'm running Xubuntu 8.10 on a Voodoo Envy 133 laptop, and I'm trying to edit my xorg.conf so that I can disable the touchpad while I'm typing. I'm trying to follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=271052&highlight=disable+touchpad+while+typing"), and I think I understand what they want me to do.

But when I attempt to edit my xorg.conf, I find that all I have is an almost blank template file there. I tried to perform the changes in the article by just typing my own input device section, but X crashed on the restart because I didn't specify a driver. I have no idea how to find out what driver I need, but that's not my main question.

20 minutes of Googling, and I cannot find a straight answer as to exactly why Ubuntu has a blank xorg.conf. Where does X get it's settings from then? I presume there's some kind of auto-config mechanism, so how does that work?

For me and all the rest of the Ubuntu noobs, will someone write a nice long post explaining this mystery?

---

### Post by philinux on 2008-11-14
[http://maketecheasier.com/ubuntu-hardy-disable-synaptics-touchpad-when-typing/2008/06/24](http://maketecheasier.com/ubuntu-hardy-disable-synaptics-touchpad-when-typing/2008/06/24)

---

### Post by jespdj on 2008-11-14
The new X.Org that comes with Ubuntu 8.10 doesn't need much configuration in xorg.conf. It can discover most settings automatically.

---

### Post by drs305 on 2008-11-14
> **tehfade said:**
> 20 minutes of Googling, and I cannot find a straight answer as to exactly why Ubuntu has a blank xorg.conf. Where does X get it's settings from then? I presume there's some kind of auto-config mechanism, so how does that work?


This will answer your question. It is taken from the [8.10 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/810").

[LIST]
[*]X.Org Input Devices

The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system).
[/LIST]

---

