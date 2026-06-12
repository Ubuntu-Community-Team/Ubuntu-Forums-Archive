---
title: "Bug on Laptop Hibernate + Attached Display + Ubuntu 10.04 LTS"
date: 2010-07-13
forum: Hardware
---

### Post by volobiz on 2010-07-13
Anyone know how to file a bug on Launchpad? I tried to do it and it completely confused me. Used to be easy to file a bug -- now you have to find the project, and it's hard to find which projects are actually active and read by the developers. Launchpad used to be cool -- now it's seeming to suck.

I love Ubuntu 10.04 LTS. I just want to make it even better. This new Monitors control panel is completely AWESOME -- much better than all previous Ubuntu releases. Now I don't have to brag about connecting monitors, but yet have to edit text files to do so. Instead, I can use the new control panel in the GUI, just like Mac and Windows.

Anyway, I found a bug. If you boot your laptop, then attach a display and configure it so you can drag windows between laptop and attached display, then put the system in hibernate -- intermittently when returning from hibernate it may switch the display orientation to the left or right of your laptop display, causing windows to need to be dragged in the opposite direction.

The workaround fix is to go into the Monitors control panel, drag the screen icons the way you want as far as orientation, and then click Apply. It will screw up (in my case) by not picking the right resolution. However, be patient with it, go back and change the resolution, click Apply, and it will fix this.

The right solution is a code fix.

---

