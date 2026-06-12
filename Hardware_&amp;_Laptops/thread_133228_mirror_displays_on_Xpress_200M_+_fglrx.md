---
title: "mirror displays on Xpress 200M + fglrx?"
date: 2006-02-19
forum: Hardware &amp; Laptops
---

### Post by jakemikey on 2006-02-19
I've got a Compaq Presario V2555US with the Ati Radeon Xpress 200M using the fglrx driver (tried ati and radeon but they didn't work at all).

I'm trying to set up easy mirroring of the main display to the VGA out port.  If I boot up with the extrenal monitor plugged in, everything works okay (although I can't get X to switch resolutions from 1280x768 to 1024x768 )  However, if I'm already logged in, plugging in the external monitor/projector does nothing.

I know there's got to be an easier way to have this happen - ie without having to restart X.  I've also done Fn+F4 with the monitor plugged in, but that also does nothing.

My xorg.conf doesn't contain anything that explicitly mentions mirroring or cloning, however I'm not even sure if xorg.conf is the problem.

I've also tried to adjust this with the "fireglcontrolpanel" command, but the mirroring options don't seem to "stick".  It tells me I have to restart X for the changes to take effect, but when I reboot, the radio buttons used to select mirroring are blank (and mirroring just doesn't work).

Any help would be greatly appreciated.

---

