---
title: "HDMI port on laptop causes screen to freeze, unplugging restores"
date: 2013-10-14
forum: Hardware
---

### Post by Ranko Kohime on 2013-10-14
I have a laptop with Intel Sandy Bridge graphics, and an HDMI port.  Previously, everything worked fine in Ubuntu, and still works fine in Windows, so I'm tentatively ruling out hardware damage.  I'm running my own blend of packages on top of a Minimal ISO install.

I was attempting to record via a Blackmagic Intensity Pro capture card from the HDMI port of this laptop.  The Intensity Pro doesn't support 1080p60 input, so I was fiddling around in xrandr trying to set a mode that the Intensity Pro would take, and it seems I've stumbled onto a bad mode.

Whenever anything is plugged into the HDMI port on the laptop, the GUI instantly becomes unresponsive, with the mouse cursor moving perhaps once every 4-5 seconds.  I cannot even switch over to a TTY, it is so bad.  However the system keeps churning away in the background, and ssh access is as speedy as always.  Very little else skips a beat on the system.  xrandr, via ssh, doesn't do so well, though, as it hangs until the HDMI port is unplugged.

As soon as the HDMI port is unplugged, everything returns to normal, the GUI is snappy again, and xrandr returns output (with HDMI1 reading disconnected, as if xrandr was waiting for the port to be disconnected just to START).

I suspect that what is happening is that Ubuntu is trying to set the last mode that the HDMI port was set to, and causing some issues.  Is there a way to force it to reset the mode?  This is persisting through a reboot, so that is unfortunately not the answer.

Thank you all for reading, and any help you may provide.

---

### Post by Ranko Kohime on 2013-11-01
Bump.  Anyone have any idea what's going on here?

---

