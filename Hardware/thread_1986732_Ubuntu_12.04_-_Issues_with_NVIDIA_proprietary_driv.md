---
title: "Ubuntu 12.04 - Issues with NVIDIA proprietary drivers and mplayer"
date: 2012-05-25
forum: Hardware
---

### Post by darthshak on 2012-05-25
I have a rather old system now (Thinkpad T61) with an older graphics card (NVIDIA Quadro NVS 140M).

I recently upgraded to Ubuntu 12.04, and have encountered a host of errors while opening mplayer with any video format. Here is the list of problems and attempted fixes - 

1) After install, I put in nvidia-current. Downloaded mplayer from the default repositories.

Result : Got a vdp_surface_create error (cant recall exactly, didnt copy out the message).

2) Downloaded the svn version of mplayer, compiled on my own. 

Result : Same error as above.

3) Removed the nvidia-current driver, used nouveau. Reinstalled the repository version of mplayer. (This, after doing a ```
sudo make uninstall
``` on the earlier version)

Result : Worked! 
Problem is, I have a dual monitor setup. Wasnt able to configure much with nouveau.

4) With nvidia-current driver, used the PPA copy of mplayer. 

Result : 
```

[   vdpau] Error when calling vdp_presentation_queue_block_until_surface_idle: An invalid handle value was provided.
[   vdpau] Error when calling vdp_video_mixer_render: An invalid handle value was provided.
[   vdpau] Error calling presentation_queue_query_surface_status: An invalid handle value was provided.
[   vdpau] Error when calling vdp_presentation_queue_display: An invalid handle value was provided.

```

5) Downgraded nvidia drivers to 295.49, 294.40, 295.33, while keeping the PPA copy of mplayer. 

Result : Same as (4).

Now, there are a couple of combinations in this list that I did not try out. Does any one have a suggestion as to what may be going on here? For most other people, just using the PPA version seems to have fixed things.

Did I not uninstall the older mplayer versions correctly? I retried all of it while doing a ```
apt-get remove --purge
``` with each copy of mplayer too. I really need my dual-monitor setup going. Ideas anyone?

---

### Post by darthshak on 2012-07-04
Bump. Had enough. Reverted back to 10.04.
Totally understand Linus' sentiments...

---

### Post by Redblade20XX on 2012-07-04
Is the NVIDIA Quadro NVS 140M still supported by the current proprietary driver?
From looking at the NVIDIA legacy driver page, [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

It seems as if support for your card ended with the **96.43.xx **drivers.

-Red

---

### Post by darthshak on 2012-07-06
Not really, I'm using the 295.* set just fine on 10.04 right now.
Strange, though. I guess I can try switching drivers again?

---

