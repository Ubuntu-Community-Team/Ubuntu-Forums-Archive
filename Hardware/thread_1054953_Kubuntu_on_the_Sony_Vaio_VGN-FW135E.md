---
title: "Kubuntu on the Sony Vaio VGN-FW135E"
date: 2009-01-30
forum: Hardware
---

### Post by Contrast on 2009-01-30
***Specs***
CPU: Intel Core 2 Duo P8400 (2.3GHz clock/1066MHz FSB/3MB L2 cache)
RAM: 3GB DDR2
Hard drive: 250GB
Video: ATI RadeonHD 3470 w/ 256MB VRAM and HDMI output
Wireless: Atheros 9000 series

***Intended uses***
Common everyday use
A little bit of gaming
On-the-go media center

I bought this laptop about three months ago, based largely on the CPU, which remains one of the best mobile processors you can get in laptops under $1000. The 3GB of RAM is 3x the amount I'd need to comfortably do what I intend on it, and the hard drive, coupled with a portable USB drive, would be plenty for my media collection. I took a leap of faith with the ATI card, based on all the talk I've been hearing in the past year about AMD improving their drivers.

On a default install of Kubuntu 8.10, everything worked out of the box - wireless and suspend included (I should note here that the driver for the Atheros wireless card is only included in Linux kernel version 2.6.27 and up, which means if you want to use an older distro, you'll need to compile your own kernel - I've used [this guide]("http://howtoforge.com/kernel_compilation_ubuntu") in the past with good results). The open-source ATI driver even used the screen's unusual native resolution of 1600x900, and the Restricted Drivers Manager installed the proprietary driver without a hitch.

***Common Everyday Use***
Overall, I'm very pleased with the performance this lappy has for general computing tasks. This is my first multi-core processor-equipped system, and it's miles ahead of my desktop in terms of speed (P4 3.4GHz w/ HT). The hard drive and DVD drives are a little slower than I'd like - fine for the most part, but the system slows to a crawl on large disk IO operations (reserving space for torrents, deleting large files, copying large amounts of data - I wonder if ext4, included as an option in Jaunty would resolve this?), and ripping/burning is a little slow, but that's to be expected on a laptop. Battery life is excellent - ~2 hours on dynamic CPU scaling, haven't checked the time on powersave mode, but I imagine it'd be a good deal better given the significant performance hit. One small thing that's easily worked around is that when using the headphone jack, sound still comes through the speakers. This can be fixed by muting the Front channel in your mixer.

***Gaming***
I'm not a hardcore gamer by any means, so as expected, the Vaio meets my needs here without any qualms. Out of Doom 3, Quake 4, Unreal Tournament 2004 and Enemy Territory Quake Wars, ETQW is the only one I can't play on max settings at a good framerate, but it still looks great with only a couple of the settings turned down from top quality.

***Media Center***
Even with the ATI driver's lack of hardware-accelerated video rendering, I'm able to play 1080p video in [Boxee]("http://www.boxee.tv") with no issues. I did have some trouble getting audio over the HDMI output in Boxee, but eventually found [the solution]("http://forums.boxee.tv/showpost.php?p=23611&postcount=17"). Aside from this and a strange resolution issue with 1080p TVs (see below), the HDMI connection works perfectly.

***ATI Woes***
When hooking the laptop up to a 1080p TV via HDMI, the results are hit or miss. The ATI Catalyst Control Center will always correctly report the TV's maximum resolution as 1920x1080, but it only sometimes allows you to select this resolution. I've yet to figure out what causes this.
One small thing I noticed, which I suspect is related to the ATI driver since I didn't run into it on my two nVidia boxes: When running Compiz, fullscreen windows aren't stacked above the panel as they should be. Another quick fix - In CompizConfig Settings Manager, enable the Window Rules plug-in and in its settings, put !(class=plasma & type=Dock) in the Above field.
One thing I've been unable to find a fix for, almost certainly caused by the ATI driver, is that trying to start a new session on a separate X server crashes the kernel (even the Magic SysRq keys don't work). This probably won't affect most people, but it's worth pointing out.
I've noticed that in desktop media players (e.g., VLC, SMPlayer, Dragon), I get some nasty playback issues I've never seen with the same videos on my other systems - interlacing artifacts, tearing, etc. Also, a compositing window manager (e.g., Compiz, KWin w/ Desktop Effects) results in lots of flickering if the video's not fullscreen. These issues are somewhat intermittent, and are largely irrelevant for me since I mainly watch videos in Boxee.
The ATI driver seems to cause much more system instability than I'm used to with a Linux OS. Where I would usually be able to just switch to a virtual console to kill a misbehaving program and get back to work, I often find that crashes bring the whole system down, forcing a hard reset.

So there you have it - an almost perfect Linux laptop, knocked down only by some ATI driver issues. If you don't plan on running a composited desktop or doing a lot of multimedia playback, you likely won't even run into these issues. Overall, if you can find a similarly equipped system with an nVidia card at a comparable price, definitely go for it, but in lieu of that, this laptop's a decent buy.

---

