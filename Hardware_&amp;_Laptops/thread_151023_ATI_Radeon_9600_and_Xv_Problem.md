---
title: "ATI Radeon 9600 and Xv Problem"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by RoboJ1M on 2006-03-27
Hi,

At the weekend I finally got round to blatting my PC and installing Ubuntu.

Now this is going to be my experimental MythTV box as well as my main desktop machine, so it's v important I get 2D/3D acceleration working.

I have an ATI Radeon 9600 (R300) and a day installing the included breezy badger version of fglrx and then replacing them with the very latest version form ati.com (followed ubuntu howto) here are the remaining problems I am having.

2D accel seems to be completely busted.

If I load the Media sink selector and test Xv after boot, the test succeeds.

but:

Totem does not use Xv for the first playing(v v slow), and then crashes out after the second playing with a device in use error.

After this the Xv test always fails

GXine also reports missing Xv but plays at an acceptable speed, but I only have a lo res test AVI.

Solutions I have tried:

I used the HOWTO in the forum to install the latest version from ATI. It worked fine although it warned me several times that /usr/src/linux appeared to be unconfigured (?)
But they were only warnings.

I have added Option "VideoOverlay" "on" and Option "OpenGL<Something>" "off" into /etc/X11/xorg.conf, this did not resolve the problem.

3D acceleration worked with both the breezy package source version of fglrx and the latest ATI version.

Debug Info:

Unfortunately I'm also without internet connection apart from here at work. I'm also v new at this do I don't know which files/command outputs to cut and paste here.

Tell me a command output to get and I can tick it on my data key tonight and post it tomorrow.

Many Thanks,

J1M.

---

