---
title: "HDMI output discoloration/overscan"
date: 2009-03-20
forum: Hardware
---

### Post by Ian Maxwell on 2009-03-20
A few threads like this have been posted before, it seems, but none with any really satisfactory resolution.

I am running Ubuntu 8.10 64-bit. I am attempting to use the HDMI output from an M3N78-VM motherboard with integrated GeForce 8200 graphics. My output device is a ViewSonic N3752w LCD television.

If I use monitor resolutions (such as 1360x768 or 800x600), the screen within X has a strong purple overlay which does not seem correctable through color settings. This is not a problem within the console, BIOS splash screen, or anything except X itself. (I don't have a Windows installation for comparison.)

If I use television resolutions (such as 1080i or 720p), there is no discoloration, but thanks to overscan the edges of the screen are cut off. I don't know if there's a way to fix this in software, but there doesn't seem to be a way on the television. Additionally, fullscreen applications that choose their own resolution still show up in all their purple glory.

I am not on the machine in question right now, so I can't post my xorg.conf, but it's just your typical system-generated stuff. I can post it when I get home.

I have found threads all over the place with people reporting similar problems. Most often the responses blame a hardware defect (either the cable or the television). This is not a good explanation since the console and BIOS splash screen are not affected. One suggestion was that the system is sending YCbCr output when it should send RGB, or vice-versa; this is possible, but I don't know of a way to correct it.

I know that others have been affected by this problem. Has anyone *solved* it?

---

### Post by bobqwerty on 2009-04-16
> **Ian Maxwell said:**
> A few threads like this have been posted before, it seems, but none with any really satisfactory resolution.

I am running Ubuntu 8.10 64-bit. I am attempting to use the HDMI output from an M3N78-VM motherboard with integrated GeForce 8200 graphics. My output device is a ViewSonic N3752w LCD television.

If I use monitor resolutions (such as 1360x768 or 800x600), the screen within X has a strong purple overlay which does not seem correctable through color settings. This is not a problem within the console, BIOS splash screen, or anything except X itself. (I don't have a Windows installation for comparison.)

If I use television resolutions (such as 1080i or 720p), there is no discoloration, but thanks to overscan the edges of the screen are cut off. I don't know if there's a way to fix this in software, but there doesn't seem to be a way on the television. Additionally, fullscreen applications that choose their own resolution still show up in all their purple glory.

I am not on the machine in question right now, so I can't post my xorg.conf, but it's just your typical system-generated stuff. I can post it when I get home.

I have found threads all over the place with people reporting similar problems. Most often the responses blame a hardware defect (either the cable or the television). This is not a good explanation since the console and BIOS splash screen are not affected. One suggestion was that the system is sending YCbCr output when it should send RGB, or vice-versa; this is possible, but I don't know of a way to correct it.

I know that others have been affected by this problem. Has anyone *solved* it?
[http://ubuntuforums.org/showthread.php?t=395101]("http://ubuntuforums.org/showthread.php?t=395101")

Give this thread a go it down grades your resolution to fix the output monitor in the xorg.conf

---

