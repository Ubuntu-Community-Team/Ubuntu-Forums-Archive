---
title: "Unable to start X-server after upgrade to Jaunty from Intrepid"
date: 2009-11-02
forum: Hardware
---

### Post by spirit_of_life on 2009-11-02
Dear all,

I had a fabulously-working Ubuntu Hardy Heron (8.04) installation on my Dell Inspiron 1420 laptop (with fully-functional compiz) until yesterday, when I decided to upgrade to Karmic via Intrepid and Jaunty. The upgrade to Intrepid went ok, though I lost compiz, but decided to carry on to Jaunty anyway, So I installed available updates and then installed Jaunty via update-manager in Intrepid, but have been unable to start the x-server ever since.

When I boot, Grub appears with a choice of two Jaunty Kernels and their respective recovery modes. My Windows vista installation also shows up and runs just fine. Running either of the Jaunty kernels gives me a kubuntu splash screen with a slick progress bar followed by a bunch of "initialising..." statements in a text terminal. This yields to a few refreshes of my display, ending on a blank black screen. The screen sort of glows, which means there is output to the screen, although no text or graphics appear. The login window never comes up. The system typically hangs at this stage, though sometimes I am able to  press and release the power button and the system shuts off after about 15 seconds.

I am able to boot in recovery mode and am presented with a blue screen containing a white dialog box that has several options (resume, clean, dpkg, fsck, grub, netroot, root, xfix). I am able to select "netroot" to drop into the root shell with networking support. I am able to install and uninstall packages from the command-line prompt that then appears. If I attempt to start the xserver using "startx" or /usr/bin/X or gdm, I get the same result as above - namely a blank screen after a few refreshes.

My video chipset is an Intel 965GM. I have the original xorg.conf backed up. Running dpkg-reconfigure xserver-xorg does not help. Replacing the driver by "vesa" does not help either.

Any ideas?

Thanks in advance,
Tanmoy

---

