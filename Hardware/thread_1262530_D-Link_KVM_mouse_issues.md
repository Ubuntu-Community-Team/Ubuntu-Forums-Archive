---
title: "D-Link KVM mouse issues"
date: 2009-09-10
forum: Hardware
---

### Post by MGaddict2000 on 2009-09-10
Obviously, I have a D-Link KVM switch which is connected to 2 computers (1: Ubuntu 9.04, 2: Windows XP) The Ubuntu computer is having problems with the mouse. When I start the computer the mouse works fine, but when I switch and come back, the mouse jumps all over the place randomly clicking on everything. This same computer dual boots Win7 and I don't have the issue there. Now for the really funny part.. It works fine on the Ubuntu Live CD. Now what sense does that make? The KVM is PS2, I tried using a PS2 to USB adapter, but then my mouse didn't work at all. I have a monitor for each computer and mostly use Synaptic between them with no issues (It's a great secret program everybody needs to look into.) but occasionally I need to use the KVM to switch. What I really don't get is why on earth the KVM works when booted from the live CD. It's like something has changed in the kernel as to how to deal with the mouse. Any help would be appreciated. Thanks.

---

### Post by Fafler on 2009-09-10
It's because the mouse uses the wrong protocol. Edit /etc/X11/xorg.conf (with the root permissions, otherwise you can't save)

Look for the InputDevice section that configures your mouse, add change/add a line like
```
Option "Protocol" "ExplorerPS/2"
```

Save and CTRL+ALT+backspace to restart the X server.

Note: ExplorerPS/2 works with my KVM switch. If you still experience problems, then man mousedrv for other options.

---

### Post by MGaddict2000 on 2009-09-10
That got it. Thanks.

---

