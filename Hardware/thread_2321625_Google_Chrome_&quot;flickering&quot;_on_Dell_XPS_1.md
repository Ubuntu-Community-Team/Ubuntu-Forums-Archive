---
title: "Google Chrome &quot;flickering&quot; on Dell XPS 13 9350 (Skylake) and Native GPUMemoryBuffers"
date: 2016-04-23
forum: Hardware
---

### Post by Christopher_Klepka on 2016-04-23
Hello folks, I've posted this to AskUbuntu (with a link on reddit) and the Chrome support forums but have not had much success yet. I tried installing Ubuntu 16.04 on my Dell XPS 13 laptop (from Windows 10) and all hardware works... but when I use Google Chrome to visit a website with a video, such as Twitch.tv, it causes the webpage itself to flicker. Well after looking at chrome://gpu, I saw multiple issues of hardware acceleration being disabled or something along those lines. So I edited some flags in chrome://flags, namely the following:

[LIST]
[*]GPU Rasterization: Enable
[*]Override software rendering list: Enable
[*]Display list 2D canvas: Enable (not sure if this did anything)
[/LIST]
[FONT=Roboto]
Now, this caused the flickering to move from the webpage, to Chrome's address and bookmark bars... no clue why. More importantly though, all the flags in chrome://gpu were fixed **with the exception of one called "Native GPUMemoryBuffers** (or something along those lines). There is no flag pertaining to this in Chrome, so I was wondering... is this something controllable through Linux? The errors when something is disabled there say it is either disabled through chrome://flags or command line by the operating system.

Right now, I'm back on Windows 10 until this is resolved, but if anyone has any other suggestions, I'd be more than willing to reinstall and try again. Like I said, I'm running a Dell XPS laptop with a i5-6200U processor (and Intel 520 graphics chip built on that). I haven't tried previous versions of Ubuntu because the wifi chip inside my computer doesn't work outside of the box, so I waited for 16.04 to be released to make it easier.

Links to other places I've asked this:
[https://productforums.google.com/forum/?utm_medium=email&utm_source=footer#!msg/chrome/CtKF2BiskT8/ax6jvFw1AgAJ](https://productforums.google.com/forum/?utm_medium=email&utm_source=footer#!msg/chrome/CtKF2BiskT8/ax6jvFw1AgAJ)
[http://askubuntu.com/questions/760042/chrome-flickering-on-ubuntu#](http://askubuntu.com/questions/760042/chrome-flickering-on-ubuntu#)[/FONT]

---

### Post by irishguy2 on 2016-04-25
Just to confirm I am seeing the same thing, on the same hardware, on 16.04. I initially thought it was a general Intel graphics driver issue so I went to 4.6 RC5 kernel as this has a fix for a known general screen flash issue but it hasn't helped. It was at that point that i realised I only ever see it in Chrome and ended up here. I'll try OP's fixes to at least move it up to the url bar which sounds like an improvement...

---

### Post by irishguy2 on 2016-04-25
FYI, this is reported as a bug, give it a star if it is happening to you (click the little at the top left, beside the bug number)...


[https://bugs.chromium.org/p/chromium/issues/detail?id=606152#](https://bugs.chromium.org/p/chromium/issues/detail?id=606152#)

---

### Post by Christopher_Klepka on 2016-04-26
Yes that is my bug report. However, I have managed to fix this is seems... please see the latest post on the bug report.

---

### Post by amos2 on 2016-11-13
This is fixed by disabling the Hardware Acceleration option in 
1. Chrome Settings >> Show Advanced Options >>  [uncheck] Use Hardware Acceleration when Available
2. Reboot Chrome

I've tried this several times and it definitely works.

---

