---
title: "S3Virge MX annoying visual artifacts"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by lava-head on 2007-03-08
I have an annoying problem with the S3Virge MX graphics card on my Clevo/Kapok 1300 laptop using Edgy. I am using Icewm as my window manager. The display creates vertical lines or splashes of colour when displaying certain images  (see typical images attached) but seems to be fine  otherwise. The display works perfectly under Windoze 98SE and also behaves perfectly from a DSL live CD. I have tried the following without success:
1. every known option for the S3Virge driver in xorg.conf without success.
2. every know resolution and colour depth setting in xorg.conf without success
3. using the vesa driver instead of the S3Virge driver without success.
4. This person's problem sounds similar to mine ([http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=78601](http://bugs.donarmstrong.com/cgi-bin/bugreport.cgi?bug=78601)) but the solution to his problem is not reported and even using the NoAccel option or the 8 bit colour has no benefit in my case.
5. using the XVesa server instead of the Xorg server, as DSL Linux does, but I still had the same visual corruptions. This suggests to me that perhaps the problem must be somewhere higher up the graphics chain.
6. I have also sent the output to my CRT instead of the LCD screen and the artifacts are still just as obvious i.e.they come from the graphics system not the display.

I don't know what to do next to resolve my problem. I have attached my xorg.conf and xorg log files for your perusal and diagnosis. The log has no errors and two warnings [(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory) (WW) System lacks support for changing MTRRs]. What can you advise me to do next?

Regards

Glen

---

### Post by lava-head on 2007-03-10
Here is some extra information that I have "detected" since I wrote the above. I booted up from a Knoppix live CD and it gave me the same kinds of visual artifacts that Edgy does. I then began to suspect that the problem was not with xorg in general but the current Debian implementation of it so I tried booting up from a modern, non-debian live CD, in this case Mandrake Move. The graphics rendering was flawless to the extent that I could test it. It now seems that Edgy's configuration of xorg does not work properly on the S3Virge MX chipset. I will attempt to notify the developers. While I wait for it to be fixed officially what do you suggest I do? I have found an unofficial backport of xorg 7.2 for Edgy here: [http://3v1n0.tuxfamily.org/dists/edgy/xorg-7.2/index.html](http://3v1n0.tuxfamily.org/dists/edgy/xorg-7.2/index.html). Should I install them and see if they fix the problem? Or should I try to compile xorg myself from source? If the latter, where can I get a howto on the matter?

---

### Post by lava-head on 2007-03-12
No answers anyone? I tried upgrading to xorg 7.2, it went smoothly but no change to the bad graphics. I have entered a bug on launchpad but there is no outcome yet. I may have to recompile xorg from source but I am not sure if I have the skill for that. Any suggestions?

Update: These artifacts are now fixed in Feisty. Everything seems to display properly now except for Realplayer video feeds which turn into changing green rectangles. Well done Ubuntu team!

---

