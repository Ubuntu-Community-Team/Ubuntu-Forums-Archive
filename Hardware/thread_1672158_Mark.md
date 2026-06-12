---
title: "Mark"
date: 2011-01-20
forum: Hardware
---

### Post by myalenti on 2011-01-20
First off... Specs:
Dell e6400 Dual core 2.4 (i3)
2gb RAM
250gb Hard drive
Nvidia Quadro NVS 160m Video Card.

Ubuntu 10.10
Kernel : Linux Late6400 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 01:41:57 UTC 2010 i686 GNU/Linux

Not running 64bit although i could.

Current Video Driver: Nivida 260.19.29

The issue:
It appears that my video card or some part of the video system becomes overly burdened after watching a video or playing a DVD. Specifically, i can start a DVD with no problems using VLC or Xine, and after about 20-30 mins, it appears that my laptop begins to warm up and video performance degrades significantly with the fan blowing. To the point where the movie is not watchable.

I can stop the movie player and kill all my apps and top or atop or any system monitor will tell me that my system is sitting around quite idle. Yet responsiveness is abysmal, and rendering anything at all seems to be a great effort to the system.

The odd part is that a simple reboot doesn't even seem to clear the issue! (If you can believe that) I actually have to do a full shutdown to kill power to everything. In fact, if i reboot from Ubuntu and boot into Windows 7, without killing power, even Windows 7 is very sluggish. I've never seen that in my life before and i've been at computers for a while now.

So i'm thinking that there is some video hardware resource that gets overloaded or drained or some sort of buffer gets filled and does not get purged, and that just rebooting does not reset this resource, it requires a full power off... 

So when this issue came about the first time, i decided that perhaps i needed a more recent nVidia driver. But the nvidia-current package does provide a very recent driver to begin with. But hey, i did the upgrade anyhow. Removed, the nvidia-current, then removed nouveau drivers and then installed 260.19.29 (so i upgraded from 260.19.09 i think)

And the issue is still present. No i'm not really surprised.
So does anyone have history with this issue? Does someone perchance know of a bug? Or  is there a setting that i need to set/change? Anything?

I appreciate the help.

Mark

---

