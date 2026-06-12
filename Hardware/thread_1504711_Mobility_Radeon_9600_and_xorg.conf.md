---
title: "Mobility Radeon 9600 and xorg.conf"
date: 2010-06-08
forum: Hardware
---

### Post by shrumhead on 2010-06-08
I just installed 10.04 Lucid Lynx on an old laptop (Dell Inspiron 8600) that I had lying around so I could play around with it at work.  I know with Lucid Lynx the video card in this laptop (Mobility Radeon 9600 Pro) is well into its "Legacy" status but even still the quality is pretty bad.  Basic display and resolution (1920x1200) work fine but when I try to play video on say Youtube or Divx, it is extremely choppy and basically unwatchable.  

I found an old solution for my exact video card that says to put the following code in xorg.conf....

```

Section "Device"
Identifier     "Configured Video Device"
Option         "AccelDFS"                               "on"
Option         "AccelMethod"                         "XAA"
Option         "MigrationHeuristic"                "smart" # "greedy" works well also
Option         "EnablePageFlip"                      "on"
Option         "EnableDepthMoves"                "on"
Option         "ColorTiling"                            "on"
Option         "FBTexPercent"                         "0"
Option         "RenderAccel"                          "on"
EndSection
```

I've also read through [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) but I must admit I'm a bit of a novice.  

My question is, can I create a xorg.conf in /etc/X11/ and simply add the above listed code?  Or does there need to be more added to make it a complete "configuration file"?

---

