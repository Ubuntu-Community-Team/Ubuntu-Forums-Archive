---
title: "Thinkpad T30 &amp; ATI Radeon 7500 &amp; Ubuntu 9.04 = slow graphics"
date: 2009-11-08
forum: Hardware
---

### Post by TroyMcClure on 2009-11-08
Hi there,

I am looking for some advice on how to get a Thinkpad T30 running at a decent speed. I am using Kubuntu on my R61 for quite some time, all with a reasonable desktop performance.

The T30 having a far less powerful processor and graphics adapter, I considered using Ubuntu with Gnome instead of Kubuntu with KDE. I installed Jaunty and now have a running system, but with an extremely low graphics performance. The system has a Radeon Mobility 7500 graphics card with 16MB of RAM. I am running with standard settings coming with the Ubuntu installation (which means an almost empty xorg.conf, no fancy parameters...), xorg-radeon and xorg-ati packages installed.

The overall performance is just very slow. Switching windows or scrolling in e.g. Firefox, marking a mail in Thunderbird - all appears very unresponsive. You can work with it, but no joy at all.

Looking at other threads, lots have such problems when direct rendering is disabled. Well, on the system it is enabled, so that should not be the problem. Various threads point at modifying loads of xorg parameters, e.g. to force to AGP 4x, use 64MB of RAM buffer, ... But none of those changes help, it is slow and stays slow.

Although my problem is probably related to 2D graphics acceleration, 3D performance from glxgears shows the dilemma as well: although it's no benchmark, it is remarkable that users report it to be running at 800 frames in 5 secs, my output is roughly 350 frames per 5 seconds.

Reducing the color depth from 24bit per default to 16bit was the only thing which helped a little - but then, Gnome does no longer show window decorations...

Any hints on how to get the T30 to a decent performance? It has to compare to the previously fine-running WinXP, and honestly, I expected Gnome to be performing better than this, not worse (especially with no eye-candy effects). Any xorg.conf samples from Jaunty proven to be working? Or is it just a fact that the performance is really lower on this setup?

Thanks for your support here,

Cheers,
Martin

---

### Post by SeePU on 2009-11-08
Can you try the latest Ubuntu Karmic 9.10 with your Thinkpad T30?

I have a T41 with Radeon 9000 graphics.  The IGP in this T41 is a bit better than the 7500 but the point is, they both use the open source Radeon driver.  I found that I need to enable safe graphics mode to just boot up.  But, then many other settings are disabled include desktop effects.  If I try to enable desktop effects, I can't.  I receive a message that 'desktop effects cannot be enabled.'

If I try to boot up in default mode, the laptop crashes at the desktop.  It is basically the same bug (it looks like) which has been existent for quite a while (as far back as Alpha 5 and 6) with little improvement.  It might be good to have a few users confirm this situation.  I hope so.  I am puzzled why Ubuntu users and devs seem so content with this situation.  I understand users with more modern hardware would be apathetic but I am surprised that no one seemed to have looked at the problem given a few bug reports and insight into the issue.

It's a shame.  I am just curious but for me, I am close to giving up but I had an idea to copy an xorg.conf file that works in another distro to the one in Ubuntu and see what happens.  I am interested in experiments but my patience is probably only enough for one or two now. ;-)

I am also asking you to try the latest Ubuntu because I figure if you do get things to work in 9.04, an update will leave you frustrated and disappointed.

P.S. I suggest leaving desktop effects turned off even if they work.   Things will be slow.  I tried on a LiveCD.  Imho, of course.

---

### Post by TroyMcClure on 2009-11-16
OK, now here's my latest status: the information on the ThinkWiki page was very useful - see [http://www.thinkwiki.org/wiki/Talk:ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/Talk:ATI_Mobility_Radeon_7500)

The part that worked was the combination of those two actions:
- wrong permissions of /dev/dri/card0
- missing option in the xorg screen settings:
--  Option		"AIGLX"		"true"

This works extremely fine on Ubuntu 9.04, it turns the Thinkpad from a useless brick into a system powerful enough for surfing, mail etc. It's a difference of day and night.

Then I did the mistake of upgrading to Karmic. Now, the Xserver tells me that I don't have enough video card memory for 24bit (interesting, it's been enough on 9.04!), and when I reduce it to 16bit, the Xserver does not start cleanly after a reboot (but complains about running low graphics mode...). Aargh!

In addition, all graphics elements using 3D are terribly screwed up (just a block of garbled pixels).

So my suggestion to Thinkpad T30 (and probably T40) users: stick to 9.04, until someone can explain what's wrong with Karmic and how to fix it. The Radeon driver seems to be terribly broken for the 7500 series.

Any help on Karmic is appreciated! All I want is to boot up without problems, a decent performance, and no screwed up graphics.

Cheers,
Martin

---

### Post by SeePU on 2009-11-16
Interesting.  Thanks for the update, Martin! :)

I hear ya regarding your update to Karmic 9.10.  I have only tried the live CD of Karmic 9.10.  Same problems although I don't know if you tried to edit xorg.conf (since nothing is there, initially) to get 3D effects running/working.  I couldn't get any combo of settings to work.  

I thought it was the Radeon driver, too, but now I'm not so sure that's entirely 100% accurate.  I tried Mandriva 2010 and desktop effects works fine albeit slow.  This is the Gnome version.  So, imho, it's Ubuntu's shoddy, weak implementation of the driver since it's like night and day.  I've read various bug reports on these issues on Launchpad and imho, Ubuntu developers have not made the issue a priority whatsoever.  Fans, admins, Ubuntu fan boys can deny it all they want, it sure seems true to me.

---

### Post by tje210 on 2010-02-04
i'm running karmic, and having the same issues.  i had made some changes to my xorg.conf, and ubuntu refused to start up... so when i started it up in low graphics mode, i found that the graphics were better than with any other settings!  so i'm keeping this, unless i find something wrong with it.  not playing any games on this lightweight setup...

---

### Post by emeraldgirl08 on 2010-02-05
Gee... I do have an xorg I used from Intrepid or Karmic.. sorry I forget! It's been awhile.
```

Section “Device”
Identifier “Configured Video Device”
Driver “radeon”
BusID “PCI:1:0:0&#8243;
Option “AGPMode” “4&#8243;
Option “AGPSize” “64&#8243;
Option “RingSize” “8&#8243;
Option “BufferSize” “2&#8243;
Option “EnablePageFlip” “true”
Option “EnableDepthMoves” “true”
Option “RenderAccel” “true”
# Eyecandy Stuff
Option “AccelMethod” “4&#8243;
Option “EnablePageFlip” “true
Option “DDCMode”
Option “SubPixelOrder” “NONE”
Option “ColorTiling” “false”
EndSection
```

I want to emphasize that you save your orignial (working) xorgs if you decide to try this! All I know is that it worked for me when I was using my T30 with it's groundbreaking 16mb of VRAM!!!

---

