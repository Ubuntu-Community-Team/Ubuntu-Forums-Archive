---
title: "HP 6626 w/Intel x3100 looks wonky"
date: 2008-09-06
forum: Hardware
---

### Post by tuberbob on 2008-09-06
Ok, I have spent quite a while searching these forums, and nothing I have found really seems to help with my issue.  I am very new to Ubuntu, so please, any responses should assume next to no experience.

I have an HP 6626US laptop dual booting Windows Vista x64 Ultimate and Ubuntu 8.0.4.1 (32 Bit).  I am using a 64 bit Windows installation to take advantage of the 4 GB of RAM I have installed.  All in all, I am pretty happy with Ubuntu, but there is one persistent issue that seems to come down to the graphics driver.  I am not running anything funky; right now all I have is a fresh install, the only change being the addition of Thunderbird for email, and a Java JRE update (which may or may not have gone off properly, who knows).

The problem is, although everything is installed and working, nothing looks quite right.  In Vista, everything is very crisp, sharp, and clean looking.  Text in particular...but for some reason, in Ubuntu, things are just a little off.  Text looks more blocky, the file browser (equivalent to Windows Explorer) doesn't look terribly clean, and the worst is Firefox.

When I am online in Firefox (the default 3.0.1 install - I did run the updater once the installation was complete), NOTHING looks right.  Text is usually too small, and again very blocky, and the one area I have noticed to be by far the worst, in fact what really drew my attention to this, is playing any MySpace apps.  They render all wrong.  I thought maybe it was a Java issue, which is why I updated the JRE using instructions at the Java site.  That did not help, and it was then I started noticing the problem everywhere, online and off.

So, all this boils down to me not being able to use the system in Ubuntu easily, because it looks awful.  If I need to, I can post some screenshots on my website, since I know I am doing a lousy job of explaining it here, despite trying to be thorough.  If anyone has any suggestions, I am willing to try anything.  Thanks in advance!

Bob

---

### Post by ssls6 on 2008-09-06
No help is probably better than my help but I'll try.

Make sure your display is set to the same resolution as it is in Windows with your LCD monitor running at 60Hz or less.  Set the minimum font size in firefox to be 14-16 points (edit-prefs-content-font-advanced-min font size)

The ubuntu intel display driver doesn't do 3D very well (for me) so don't use enhanced display effects.

---

