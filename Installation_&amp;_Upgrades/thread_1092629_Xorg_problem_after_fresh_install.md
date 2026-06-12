---
title: "Xorg problem after fresh install"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by t0mppa on 2009-03-10
Hello,

I'm having some trouble installing Ubuntu 8.10 on dualboot with Vista on my Acer laptop.

System info:
AMD Turion X2 Dual-Core Mobile RM-70 2.00 Ghz
4GB RAM
ATI Mobility Radeon HD 3470

Here's the history of my problems:

started first with trying to run from a Live CD, it failed to boot into the XWindows, just dropped me into a command line console. Same thing happened when trying to install.

Then tried burning another CD at lowest possible speed, check MD5's and other quick fixes found through google. None of them worked though, so tried the same CD's in another computer and everything worked just fine there.

After this I got tired of reburning CD's, which according to the posts I read on this forum work maybe 20% of the time and instead grabbed a USB stick, downloaded the alternative installer ISO as a Torrent (was recommended, since Torrents evaluate MD5 sums of each piece they DL on the fly and thus avoid download problems) and used UNetbootin to get the job done.

This worked wonderfully and I managed to finish up the installation. However, now I have a few problems. When trying to start up in Ubuntu, it still fails to get into XWindows and keeps dropping me to the console.

Running 'startX' gives:

> X.Org X Server 1.5.2
Release Date: 10 October 2008
X protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-10-server i686 Ubuntu
Current Operating System: Linux tommi 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
         (++) from command line, (!!) notice, (II) informational,
         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time Tue Mar 10 22:05:36
(==) Using config file: "/etc/X11/xorg.conf"
Primary device is not PCI
(EE) No devices detected

Fatal server error:
no screens found
giving up.
xinit: Connection refused (errno 111): unable to connect to X server
xinit: No such process (errno 3): Server error.

Checked the Wiki and it says the latest XOrg build was released on September 23, 2008 which is earlier than the one above states being released, so guess that's not a problem.

And bottom of the Xorg.0.log:

> Primary device is not PCI
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"

(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.5.0, module version 1.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 4.1
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is:
(WW) Falling back to old proble method for vesa
(EE) No devices detected.

So, I'm guessing it's some sort of an issue with the Graphics card drivers?

Also a secondary issue is that the install left GRUB on my USB stick instead of my HDD, so if I want to be able to boot to either of the OS's I need to put that USB stick in. That seems kind of a bug with the UNetbootin, known issue or worth reporting somewhere on its development?

---

### Post by avtolle on 2009-03-10
It is trying to load the generic Vesa driver, and failing as it is not detecting the graphics card. On startup, at the bottom of the login screen, is an area titled "Session". Click on that to open it, one option should be failsafe mode (or something like that). Select that, and log in to see if you can get to a desktop. Once there, you will need to install the driver for your card (there should be a pop up talking about proprietary drivers needed, or words to that effect).

Another thing to try when dropped to the console would be to type xfix and see if that does anything.

---

### Post by t0mppa on 2009-03-10
Thanks for the quick reply!

Nothing about session on the start up, plus it looks rather shell like, don't think mouse is even present there, so not much clicking to do.

> $ xfix
-bash: xfix: command not found

I downloaded ATI's newest Linux driver and trying to install that now from the shell.

[EDIT] Finally managed to install the driver after having to google around a bit how to work with USB sticks on the shell and other stuff, but I got my XWindows up and running now, thanks for the help anyway!

Oh and you were right about the restricted drivers part, it shows up now, a little too late though. :/

---

### Post by Jphenow on 2009-03-12
I get a similar issue...but I'm in the middle of a reinstall so I can't just go into shell and install a new driver. I'm on the Live Disc

---

