---
title: "Multiple Monitors in 14.04"
date: 2014-09-30
forum: Hardware
---

### Post by jess7 on 2014-09-30
Hello,

I have a Dell Precision T3600 desktop, and I have 3 monitors connected. I have 2 of the following video controllers...

VGA compatible controller: NVIDIA Corporation GF108GL [Quadro 600]

The monitors are connected to 2 DVI ports and one DisplayPort. I cannot rotate one of the DVI monitors (identical to the one connected to DisplayPort) using the Displays settings. When I click on the box to rotate, it just highlights "Normal" and will not let me select an alternative from the dropdown menu. Has anyone had a similar problem to this? How should I fix this?

---

### Post by jess7 on 2014-10-01
As an update, I tried a proprietary driver from NVIDIA and this was worse - the 3rd monitor, while "on" is not functioning. I get a black x cursor when I mouse over it. I tried nvidia-settings and that monitor is "yellow" in the display configuration.[ATTACH=CONFIG]256892[/ATTACH]
I tried saving the config file, and restarting x, but with no luck. Also, it won't save my monitor configuration in general; whenever I restart, the screen rotation is reverted as well as the monitor positioning. For the right side monitor, there is no option to have it as the same x# screen as the other 2; it's either a new one, or disabled.

---

### Post by didier5 on 2014-10-01
Your case is interesting for me.

You config is more unusual than mine.
I use an horizontal 1600x1200 and a vertical 1680x1050 + NVIDIA.

I had to stop and to stay with one monitor (unstable - crash)
I suggest you to try Lubuntu ( that what I did )

Or to test only with horizontal monitors. Vertical seems to be the weak point.

Maybe you should contact directly NVIDIA. That what I'm planning to do.
Fortunately, I've kept an XP config which works. I will ask NVIDIA the equivalent driver.
What XP can do since 2006, ubuntu should do ?

---

### Post by didier5 on 2014-10-05
As I did, you merge different physical monitors and orientation under the same X0. Such incompability can't be saved in xorg.conf.
You have an empty area within X0 area (inside dashed square).

Now I've selected one X logical screen per physical monitor. And then I've selected "xinerama" to link everything.

The documentation and manual are too succinct. Errors misses. Maybe some little bugs.

Now it's stable, but I stil have twice the shortcuts on the desktop. Cause : combination of vertical and horizontal monitors.

---

