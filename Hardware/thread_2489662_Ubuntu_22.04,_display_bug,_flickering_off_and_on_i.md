---
title: "Ubuntu 22.04, display bug, flickering off and on in fullscreen, nvidia+display scale"
date: 2023-08-06
forum: Hardware
---

### Post by nullbio on 2023-08-06
Hi. 

Here's some of my system details: 

Ubuntu 22.04 x64
Display: x11 server: X.Org v: 1.21.1.4 compositor: gnome-shell v: 42.9
Linux pc 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Thu Jul 13 16:27:29 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
Nvidia proprietary drivers (version 535.86.05)
Graphics cards: RTX 4090 & RTX 3090Ti
Dual displays: 48inch LG CX1 as primary (4k @ 119hz) HDMI, secondary 27inch (4k @ 60hz) DP
X11 display manager set to: gdk3

I have nouveau drivers blacklisted. For some reason the official Ubuntu nvidia drivers were not compatible with my system, hence why I'm using the proprietary ones.

I was previously on an older version of the proprietary drivers, but I noticed a bug, whenever I go full screen in vlc player watching a video my primary display keeps turning on and off/flickering on and off, displaying "The Instant Game Response is launched" message on the monitor (which is an LG screen pop-up basically saying that ALLM is activated) in a loop.
When investigating why this was happening and what "The Instant Game Response is launched" means, I found out that it means ALLM (auto-low latency mode) is activated on the screen. Apparently Playstations have caused this problem in the past too with this display, according to online posts I have found related to this problem, and is related to VRR (g-sync) and ALLM. If I disable gsync in Ubuntu, the problem does not occur because ALLM is never activated on the screen, so I don't get the flicker. However the choppiness makes watching videos untenable. 

I suspected it might be a bug in the proprietary nvidia drivers, so I updated to the latest version of the drivers. The bug is still present. HOWEVER, I noticed that in my Gnome Screen Display settings, if I set my screens scale to 100%, the bug does not occur. It's only when I'm scaling my monitor to 125% that this problem happens. So I'm not sure if this is a Ubuntu bug, a bug with the nvidia proprietary drivers, or a combination of both. 

Here's a reddit thread where someone had a similar problem with a 3080 and nvidia drivers (gsync): [https://www.reddit.com/r/OLED/comments/m4k6wb/instant_game_response_activating_over_and_over/](https://www.reddit.com/r/OLED/comments/m4k6wb/instant_game_response_activating_over_and_over/)

Here's an example of the popup message on the screen: [https://img.nerdburglars.net/wp-content/uploads/2022/05/20220504_211915.jpg](https://img.nerdburglars.net/wp-content/uploads/2022/05/20220504_211915.jpg) -- although in my case it's just a black picture alongside it.

I have no issues on Windows when this is triggered on my display, only in Ubuntu, and only when scaling is set to 125%. Works fine at 100% scaling (although it doesn't display the pop-up at 100% scaling, indicating that perhaps it's not even activating ALLM for some reason at this scaling in fullscreen).

Does anyone have any suggestions on where I should take this from here? Happy to post a message somewhere else or use a bug report or something, just not sure how all of this works. Thank you.

---

