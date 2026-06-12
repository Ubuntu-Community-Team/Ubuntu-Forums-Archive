---
title: "Does AMD/ATI 790GX IGP work in Jaunty 64 w/ 2 monitors/xinerama? display overlap bug"
date: 2009-08-07
forum: Hardware
---

### Post by GeekLove_JavaStyle on 2009-08-07
Hello,
This is a duplicate of:
[http://www.phoronix.com/forums/showthread.php?t=18417](http://www.phoronix.com/forums/showthread.php?t=18417)

Hello All,
I am trying to run 64-bit Ubuntu 9.04 Jaunty Jackalope with 2 monitors in xinerama and my embedded 790GX IGP. I am running a phenom 2 955 CPU and a 1600x1200 monitor in DVI and a 1920x1200 monitor in HDMI.

I installed the latest catalyst drivers from ATI's website. When I boot up, it appears normal.

My left/primary monitor (with toolbars) works great. When I move a window to the secondary/right monitor, I can't move the window all the way to the right.

When I maximize a window on the left/primary display, everything works as expected.
When I maximize a window on the right/secondary display, it maximizes, but the window is shifted to the left by about 400 pixels or so. I see desktop to the right in the monitor and the window overlaps into the left by the same number of pixels.


When I disable xinerama, the display works correctly.  

Here's what I did:

   1. fresh install of Jaunty 64
   2. update everything
   3. enable proprietary AMD driver from Driver Manager in Ubuntu
   4. display bug

Tried installing latest driver from ATI...same issue.

Tried installing a Radeon 3450 graphics card in the PCIe slot and had the same result.

On Windows, dual monitors works (as does hybrid crossfire), so I know it's not the hardware.
[LIST=1]
[*]Is there a name for this bug? I'm having a hard time researching it as I don't know how to describe it. Surely I'm not the first person to experience this and there's got to be a term I can google to find advice.
[*]Does the 790GX work in Jaunty 64-bit in xinerma for anyone? If so, did you do anything special to get it working?  Could you please paste your xorg.conf?
[*]Has anyone gotten a Radeon 3xxx card working in Jaunty 64 w/ xinerama? If so, did you do anything special to get it working?
[*]Has anyone gotten any Radeon card working in Jaunty 64 w/ xinerama? If so, did you do anything special to get it working?
[/LIST]


Any help is greatly appreciated.

Steven

---

