---
title: "Dell Latitude d630 - wireless &amp; docking station"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by pnips on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=573330](http://ubuntuforums.org/showthread.php?t=573330) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello all,

I installed gutsy yesterday (so glad to be rid of windows). A few issues, though.

(1)
My wireless worked out of the box, but the sound didn't. I followed the directions here:

[http://ubuntuforums.org/showthread.php?t=573330](http://ubuntuforums.org/showthread.php?t=573330)

and now my sound works, but my wireless doesn't. The link just listed predicts this problem, but the fix listed didn't work for me. I suspect the problem may have something to do with the message, when I try to open the restricted drivers manager, that I need to install the package linux-restricted-modules-2.6.23. Problem is, I can't seem to find that package anywhere.

(2)
The other problem is that my port replicator doesn't work almost at all. When I plug in the already booted computer, it recognizes that it's not on battery power, but that's it. The external screen, mouse, keyboard, sound and network cable don't pick up. Also, the laptop keyboard stops working, and the touchpad, although it still works, goes all wonky (jumps around the screen seemingly at random).

When I boot the computer already attached to the port replicator, the external monitor works (although the resolution is off, and I can't make dual screen work, these would be problems for another day), but still no keyboard, mouse, sound & network. Searching the forum seems to indicate this is not a common problem, so I'm stuck.


Any help would be appreciated. If you need the output of any programs or the contents of any files, please give the command line instruction or the location of said file, as I'm a bit of a n00b.

Thanks,
pnips

---

### Post by wutsch on 2007-10-22
hi,

i'm having exactly the same problems with the docking station like you, except that i'm on a latitude d830, which should not make much of a difference :)
Any suggestions concerning docking and ubuntu would be much appreciated

---

### Post by primate on 2008-02-26
Also having problems with docking station/port replicator.  Using Dell Latitude D630 and Dell D/Port Port Replicator.  External mouse and keyboard work fine, but not monitor.  Have NVIDIA Quadro NVS 135 M video card.

---

### Post by primate on 2008-02-26
I finally figured out how to get my external monitor (Dell 9100FP) working with the port replicator.  After setting up the NVIDIA video card, I changed the NVIDIA settings in the following manner to get external monitor working while attached directly to the laptop*:

1.  At command line, type:  gksudo nvidia-settings
2.  In NVIDIA X Server Settings dialog box, select X Server Display Configuration
3.  In Layout window, click on non-LPL (i.e., external monitor) display (LPL refers to the laptop display)
4.  Click on Configure button & select TwinView
5.  For the Position option, select Clones
6.  Click on Save to X Configuration File button
7.  Retart

*After adjusting the NVIDIA settings with the laptop attached directly to the external monitor, the external monitor attached via the port replicator also worked.

When switching between using an external monitor and the laptop display, you may need to go back into the NVIDIA X Server Settings to adjust the resolution using gksudo nvidia-settings

Good luck!

---

### Post by hardynovice on 2008-05-09
> **primate said:**
> I finally figured out how to get my external monitor (Dell 9100FP) working with the port replicator.  -snipped-
1.  At command line, type:  gksudo nvidia-settings
2.  In NVIDIA X Server Settings dialog box, select X Server Display Configuration
3.  In Layout window, click on non-LPL (i.e., external monitor) display (LPL refers to the laptop display)
4.  Click on Configure button & select TwinView
5.  For the Position option, select Clones
6.  Click on Save to X Configuration File button
7.  Retart
-snipped-

After installing Hardy and then the nvidia drivers on my latitude D830 (with NVS135 nvidia card) I was unable to use the port replicator.  I followed Primate's setting alterations above and that fixed the problem.  

Thanks!

---

