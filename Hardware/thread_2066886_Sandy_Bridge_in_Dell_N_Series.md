---
title: "Sandy Bridge in Dell N Series"
date: 2012-10-05
forum: Hardware
---

### Post by akoskm on 2012-10-05
Hi!

I just come over this post: [Enabling Sandybridge New Acceleration]("http://ubuntuforums.org/showthread.php?t=2057512").
After adding that config file I noticed that my Intel Graphic card is shown correctly in System Settings > Details

[IMG]http://i50.tinypic.com/345nd54.png[/IMG]

I also noticed that

glxgears reports:
```

18642 frames in 5.0 seconds = 3728.317 FPS
19572 frames in 5.0 seconds = 3914.397 FPS
18505 frames in 5.0 seconds = 3700.850 FPS
19610 frames in 5.0 seconds = 3921.791 FPS

```

while with **optirun glxgears** I get only
```

4329 frames in 5.0 seconds = 865.716 FPS
4059 frames in 5.0 seconds = 811.582 FPS
4247 frames in 5.0 seconds = 849.052 FPS
4249 frames in 5.0 seconds = 849.627 FPS

```

which makes no sense to me. AFAIK optirun should run glxgears with my GeForce GT 525M card so I expect better performance.

Should I leave this configuration file on? How this will impact the overall performance of my laptop and battery lifetime?

---

