---
title: "Problem using 3 screens (onboard VGA and PCIe card)"
date: 2010-01-01
forum: Hardware
---

### Post by ChrisWebb on 2010-01-01
Well first of all, Happy New Year one and all!

I have been working on a dual monitor setup for many moons now and have had no problems running my two 1280x1024 flat panel monitors on my GeForce 6600 PCIe graphics card. I am currently running Karmic x64.

I now have a third monitor that I have connected to the onboard graphics (a GeForce 6100). This third monitor has a native resolution of 1280x720. No problem thinks I; I'll just run nvidia-settings and detect the third monitor, put it to the right of the existing twinview display and all will be tickety-boo. Not so. I have metamodes set up for the twinviewed 6600 adapter otherwise I get nothing other than 640x480, and I like fullscreen apps to stay on the left monitor rather than stretching over two. While these metamodes shouldn't affect the onboard graphics the resolution being pumped to the third display seems to be 1280x720 panned over 1280x1024. Worse still the desktop on this monitor is corrupted because it looks like 1280x720 stretched over 2560x720 (double width pixels in effect). Thus the mouse position doesn't relate to what's on screen, and things like menus are corrupted. This distortion is eliminated if compiz is turned off, but the panning remains.

So in summary how can I:
1) Disable panning on the third monitor and retain the native resolution?
2) Get the blooming thing to work with Visual Effects enabled?

I look forward to any suggestions!

---

### Post by HarrisonNapper on 2010-01-08
Compiz is known to be a little bit unstable when it comes to a lot of things, so there may be a line you have to add to compiz that helps with the 1 over 4 pixel issue. That being said, most of the other stuff should be taken care of in the nVidia config dialogue and by restarting X once you've gotten everything entered in. I've actually never tried with more than 2 screens and I use KDE to boot, but this wasn't pulling a response, so I figured I'd try and throw something out there :)

Cheers.

---

### Post by ChrisWebb on 2010-01-08
Thanks for posting, I'll investigate the Compiz issue when I have more time.

I too thought the nVidia config would handle this OK, I even forced it to re-detect from fresh and still got the same result. Maybe it's because I'm running the two main screens in Twinview; maybe it'll work correctly with Xinerama?

---

