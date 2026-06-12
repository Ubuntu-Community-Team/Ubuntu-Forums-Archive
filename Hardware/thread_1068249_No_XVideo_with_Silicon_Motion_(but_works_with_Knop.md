---
title: "No XVideo with Silicon Motion (but works with Knoppix). Please help."
date: 2009-02-12
forum: Hardware
---

### Post by Psychav on 2009-02-12
I'm new to Linux and wanted to inject a bit of life into an old IBM Thinkpad 240X subnotebook with Silicon Motion Lynx EM+ graphics. I chose a custom install of Xubuntu v8.04.1 and installed not much more than Fluxbox and VLC.

Unfortunately, when running VLC and using 'xvideo' as the output module I get the following:
> X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  86
  Current serial number in output stream:  87

Similarly, when using the Kaffiene player I get a blue playback area but when I boot into Knoppix v5.1.1, Kaffiene will work and the video is accelerated.

Can someone please help me diagnose why XVideo isn't working and how I might be able to fix the problem? I've attached xvinfo output, Xorg.0.log and xorg.conf from both distros as a starting point. Let me know if I should add any other information.

Thank you for your time and ideas.

---

### Post by Psychav on 2009-03-03
I retried using the standard xubuntu desktop and used 'X -configure -probeonly' to get a good xorg.conf but still got the same issues.

Then I read here ([http://www.phoronix.com/scan.php?page=news_item&px=NjY4Ng](http://www.phoronix.com/scan.php?page=news_item&px=NjY4Ng)) that new to version 1.6 of the Silicon Motion driver is XVideo support. No wonder therefore that XVideo doesn't work as xubuntu 8.04 includes version 1.5.

So I tried Intrepid (8.10) but that didn't work so well. There is a new bug here that causes a "AddScreen/ScreenInit failed for driver 0" error ([https://bugs.freedesktop.org/show_bug.cgi?id=18816](https://bugs.freedesktop.org/show_bug.cgi?id=18816)).

I tried installing the .deb files from Jaunty in Intrepid and that just got me a black screen. (It was worth a try I guess)

I've reverted back to my image with 8.04 and XCFE.
Is there a way I can just install the latest 1.7 Silicon Motion driver on 8.04?

---

### Post by Psychav on 2009-03-09
I tried Debian Lenny (5.00) as it includes version 1.6 of the silicon motion driver and i still get the same problem. :(

---

### Post by Psychav on 2009-04-29
No luck with Jaunty either!

I get a black screen (no backlight either) after installing LXDE and it tries to load a graphical login.
I guess this problem also still exists...
[https://bugs.freedesktop.org/show_bug.cgi?id=18816](https://bugs.freedesktop.org/show_bug.cgi?id=18816)

But the black screen problem is fixed, so how to get the fix in Jaunty so I can try XVideo with it?

---

