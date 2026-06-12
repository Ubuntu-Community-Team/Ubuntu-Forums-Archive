---
title: "DVI stopped working after going to sleep"
date: 2011-04-02
forum: Hardware
---

### Post by justin_p on 2011-04-02
I have been using my LCD on a DVI cable for at least 6 months without issue.  

This morning I did a fresh install of 10.10.  Ran the updates and rebooted into the new kernel.  Installed NVIDIA drivers.  Rebooted.  No issues.  Installed my some programs and after completed I went to workout for about an hour and a half.  

Upon returning home I hit the space bar to wake up the Computer (standard tower).  The computer came on but the monitor will not display anything.  I have had this issue in the past but was able to fix with a reboot and re-configure the screensaver.  

On reboot the monitor doesn't display anything.  The color of the light changes from orange to green indicating that it's receiving a signal (no "check connection" message from monitor).  But nothing.  I am sure its a hardware issue, I just don't know how to fix.  Set up is nvidia > dvi > monitor.  Google gave no love.  

Any suggestions would be great.

Hardware:
2.8 GHZ Intel Dual Core (x64)
Nvidia Gefore 210 
Samsung Syncmaster 171t

As stated, all worked well earlier in the day.  

Thanks.

---

### Post by justin_p on 2011-04-02
Yes, I am replying to own thread in case someone else has the same issue.  I think there was a conflict between the Screensaver and Power Management utilities in regards to power manager controlling the when/if the monitor is turned off.  I had it set for 15 mins.  The Screensaver was set for 10.  I changed the power manager settings to 5.  We'll see what happens.

I got the monitor working again but powering down and unplugging the cpu and monitor, leaving the DVI cable in.  Wait an hour.  Plug in the CPU then the monitor.  Everything came up.

---

### Post by justin_p on 2011-04-03
Still no luck after the computer went to sleep.  I added to a comment here:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/34043.]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/34043")

If you are having similar issues let the devs know.

---

