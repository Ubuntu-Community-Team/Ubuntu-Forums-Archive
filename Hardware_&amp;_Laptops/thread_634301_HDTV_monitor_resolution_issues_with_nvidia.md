---
title: "HDTV monitor resolution issues with nvidia"
date: 2007-12-07
forum: Hardware &amp; Laptops
---

### Post by iPLAYwithFIRE on 2007-12-07
I'm not making a *please help me!!!* post.  I really have been trying the past few days to find the correct solution to my problem.

I've made little progress in trying to get the correct resolution for my tv/monitor.  I've managed to mess up the xorg.conf file royally and couldn't get it to startup.  

And now I've managed to have a small breakthrough but it still hasn't solved my problem:
in nvidia settings it doesn't give a 1366x768 resolution.  So the default it chooses is 1280x768 which of course stretches it and makes the fonts terrible.  But in the settings i set the panning resolution to 1366x768 - it works but i have to mouse over to the sides of my monitor and it pans over to the remaining pixels.  It's pretty annoying.  Everytime I try to configure the xorg.conf file to something like
```

    Option         "metamodes" "1280x768 @1366x768 +0+0 (this is the one it successfully edits); 1366x768 +0+0 (this is my edit); 1024x768 +0+0; 800x600 +0+0; 720x400 +0+0; 640x480 +0+0"

```
it never recognizes my edit.  in fact when I look back in the file it says this:
```

# Removed Option "metamodes" "1280x768 @1366x768 +0+0; 1366x768 +0+0; 1024x768 +0+0; 800x600 +0+0; 720x400 +0+0; 640x480 +0+0"

```

my video card is GeForce FX 5200 (old I know)....

what's the best way to make nvidia recognize my screen resolution of 1366x768 without panning?  it works fine with the native resolution when the nvidia driver isn't enabled...

---

