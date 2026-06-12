---
title: "Ubuntu 13.04 Volume Significantly quieter than when running windows."
date: 2013-05-05
forum: Hardware
---

### Post by apastuszak on 2013-05-05
I am running Ubuntu 13.04 on a ThinkPad T420, and the volume is significantly quieter under Ubuntu than it is under Windows.  I ran alsamixer, and it won't let me crank the volume up any louder.  I can go into the sound applet crank the volume to 140%, but even that is quieter than the Windows.

Has anyone else seen this, or know how to correct it?

---

### Post by TenPlus1 on 2013-05-06
My volume was a tad low also and I'm using Alsa instead of PulseAudio but when I muted my computer's digital outputs and rebooted my volume increased...

---

### Post by SeTiDaYeTi on 2013-06-27
> **apastuszak said:**
> I am running Ubuntu 13.04 on a ThinkPad T420, and the volume is significantly quieter under Ubuntu than it is under Windows.  I ran alsamixer, and it won't let me crank the volume up any louder.  I can go into the sound applet crank the volume to 140%, but even that is quieter than the Windows.

Has anyone else seen this, or know how to correct it?

Same problem for me on an HP Folio 13. I'm yet to find a suitable solution to it.

---

### Post by apastuszak on 2013-06-27
I need to try a Fedora Live CD and see if the problem is Ubuntu specific, or because of the sound architecture in the kernel.

---

### Post by andrew-beals on 2013-10-13
> **apastuszak said:**
> I need to try a Fedora Live CD and see if the problem is Ubuntu specific, or because of the sound architecture in the kernel.

It's Ubuntu-specific.  Some jackhole thought it would be a good idea not to let you put the volume all the way up - probably because some people use earphones and the current practice is to peg it at 66% to 75% of max volume.  Go into the Sound Settings… under the speaker icon and you can move it past "100%".

---

### Post by apastuszak on 2013-10-13
I saw that.  Problem is, you can't get it above "100%" using the volume keys or the applet.  Very annoying.

---

### Post by cdysthe on 2013-10-29
I agree, this is very annoying. They should have an option to control the volume fully with keys or from the notification volume control. Now i have to open sound settings to get it lound enough. I recently ran Windows on this laptop for a while and I was able to turn the volume up fully with buttons or volume control.

---

