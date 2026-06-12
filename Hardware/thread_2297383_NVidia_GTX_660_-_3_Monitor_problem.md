---
title: "NVidia GTX 660 - 3 Monitor problem"
date: 2015-10-03
forum: Hardware
---

### Post by squweez on 2015-10-03
Hi,


I'm having trouble with setting up my three monitors with Ubuntu 14.04 and Geforce GTX660.


**1. Problem**
My third screen (26" LG 16:9 Display) is not correctly recognized and therefore only possible to use in 4:3 mode.
It is connected via the Displayport of the GPU with a Displayport to HDMI adapter and via HDMI to the screen.


**2. Problem **
(not that bad, since I could script the solution and run it on startup)
The screen configuration (Positioning, resolution) is not stored. Neither when done via nvidia-settings nor when done with the "normal" display setting from Ubuntu.


**Details about my setup:**

[LIST]
[*]Main Screen: Benq 24" (16:9), connected via HDMI
[*]Second Screen: LG 19" (4:3), connected via DVI
[*]Third Screen: LG 26" (16:9), connected via Displayport-HDMI adapter through HDMI (see above)
[/LIST]

```

lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GK106 [GeForce GTX 660] (rev a1)

```

Ubuntu 14.04, installed Unity, but using Gnome desktop environment


**Things I've tried so far:**

[LIST]
[*]Installing every driver listed under "additional driver", just to make sure that none of those work.
[*]Installing the latest driver from the Nvidia Page, which leads me in a funny flashing tty, where I can only get rid of it again in recovery mode.
[*]Installing Ubuntu Gnome 15.04 -> This actually somehow "worked". In the beginning all 3 Monitors where detected correctly, BUT everything was kinda laggy, and as soon as I started a program, the system would freeze to a point where I can move the mouse, but nothing else (Couldn't even go to TTY). Then I installed graphic drivers under Ubuntu Gnome 15.04. That lead me back to the same problem I have on Ubuntu 14.04.
[/LIST]


I really appreciate every help, that leads me to a solution of the problem.

(crosslink reddit: [https://www.reddit.com/r/linuxquestions/comments/3nbwji/ubuntu_nvidia_gtx_660_3_monitor_problem/](https://www.reddit.com/r/linuxquestions/comments/3nbwji/ubuntu_nvidia_gtx_660_3_monitor_problem/)
 crosslink nvidia forum: [https://devtalk.nvidia.com/default/topic/522788/gtx-660-with-3-monitors/?offset=13](https://devtalk.nvidia.com/default/topic/522788/gtx-660-with-3-monitors/?offset=13))

Thanks in advance,
SquweeZ

---

