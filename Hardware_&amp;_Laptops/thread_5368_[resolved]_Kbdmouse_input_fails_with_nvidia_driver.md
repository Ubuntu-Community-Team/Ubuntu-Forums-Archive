---
title: "[resolved] Kbd/mouse input fails with nvidia driver"
date: 2004-11-18
forum: Hardware &amp; Laptops
---

### Post by HungSquirrel on 2004-11-18
I swapped out my ATI card for an Nvidia GeforceFX 5700LE.  Following the [instructions](http://www.ubuntuforums.org/showthread.php?t=3713), I removed the fglrx drivers and replaced them with nvidia-glx.  I removed fglx from /etc/modules and added nvidia.  I edited my XF86Config-4 to use the regular nv driver at first to test the card.  So far so good!

I replaced the driver entry with nvidia and restarted X.  Then everything went to crap.  After about five seconds at the GDM, keyboard input stopped working.  The cursor in the login field stopped blinking.  I could still move my mouse, but mouse clicks on the Shutdown menus, etc. did not register.

The X log shows no error lines, but the following warning lines:
```
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) NVIDIA(0): Failure reading EDID parameters for display device CRT-0
(WW) NVIDIA(0): Not using mode "1152x768":
(WW) NVIDIA(0):   horizontal sync start (1178) not a multiple of 8
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
```

I am attaching my XF86Config-4 and the output of dmesg.

Has anyone encountered such an issue before, and how might I go about resolving it?

---

### Post by HungSquirrel on 2004-11-18
This is an issue with the nvidia driver and the Ubuntu team need not concern itself with it.  Apparently, lots of people from lots of distros have the problem, if [this thread](http://www.nvnews.net/vbulletin/showthread.php?t=31858) at the nV News Forum is any indication.

My solution was I had to disable 4x AGP support in my BIOS.  Naturally I am not pleased at all about this because the card runs much slower than it should.

The good news is, unlike the ATI drivers, the Nvidia drivers run Deus Ex in Cedega at a great framerate.


Why can't I get a break when it comes to 3D drivers in Linux?  [img]http://www.ubuntuforums.org/images/icons/icon8.gif[/img]

---

### Post by pnoewbe on 2006-10-09
I just tried the nvidia driver. I have geforce4 4400 or something. I don't want to bother to find out exactly what card I have right now.

The mouse seems to act up when the startup music plays. Does the audio driver load and then hog cpu?

My mouse cursor locks or disappears for five seconds or so, then comes back and I can move it around for five seconds, then it goes away. I can't click on anything, though. So that's like it's not getting enough cpu time.

I'll try the bios agp setting like you did.

---

