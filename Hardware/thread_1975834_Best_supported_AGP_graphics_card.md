---
title: "Best supported AGP graphics card?"
date: 2012-05-07
forum: Hardware
---

### Post by jamesbeat on 2012-05-07
I have an old desktop system that I have hooked up to my TV to watch movies and use skype.

It's an old machine, but from the specs, It should be working acceptably with Ubuntu (I'm using 10.04 because I like Gnome the way it was then)

Video was running horribly, so I upgraded the processor from a P4 1.6Ghz to a P4 2.6Ghz.
While I have noticed a dramatic difference in speed while performing general desktop tasks, and video jas improved a great deal, it's still struggling.
I am also upgrading the memory from 512Mb to 1024Mb, but it hasn't arrived in the mail yet.

When I used system monitor to see what was happening when I played videos, it told me that cpu was running at 98-100%.
I expected the new processor to improve this, but although video is playing a lot better now, it is still choppy in fullscreen and using 100% of the cpu.

Memory usage has been around 50% with both processors, which I found a little surprising.

I'm thinking that I need to do something about the graphics card.
At the moment, I have an ATI Rage 128. There are some drivers installed specifically for it, but I understand that ATI cards aren't very well supported.

I looked on ebay and there are loads of old AGP cards available for cheap.

What would be a good one to go for?


The specs:
Dell Dimension 4300
Pentium 4 2.6Ghz
512Mb RAM, soon to be 1024Mb
ATI Rage 128 AGP graphics card
Ubuntu 10.04LTS

Another point that occurred to me was that these old graphics cards might struggle with such a large display.
Would going down to a slightly lower resolution help?
I wouldn't really mind taking a bit of a hit with resolution, as I'm sitting further back from the screen than I would with a monitor, so everything would be easier to see.
Only thing is, I tried lower resolutions, and all I got was a nice view of the top left corner of my desktop, ie. the desktop didn't resize to fit the lower resolution.

I should also mention that I tried several distros; Lubuntu and Xubuntu, Bodhi, Mint etc and all gave this problem.

---

### Post by mips on 2012-05-08
Sound like you are looking for a nvidia card where you can offload the video decoding to the GPU.

[http://en.wikipedia.org/wiki/VDPAU#Device_drivers_and_hardware_supporting_VDPAU](http://en.wikipedia.org/wiki/VDPAU#Device_drivers_and_hardware_supporting_VDPAU)
[http://www.mythtv.org/wiki/VDPAU#Supported_Cards](http://www.mythtv.org/wiki/VDPAU#Supported_Cards)

So you might want to look out for one of these with a AGP interface which I suspect will be hard to find,
GeForce 8500 GT
GeForce 8600 GS
GeForce 8600 GT
GeForce 8600 GTS
GeForce 8800 GS
GeForce 8800 GT
GeForce 8800 GTS 512

If your PC has PCI slots (no not PCIe) you could also look at the newer GT430 & GT520 PCI cards if your budget allows.

---

### Post by jamesbeat on 2012-05-09
Thanks for the advice, but I managed to solve the problem a different way- I got rid of pulseaudio.
I realised that it was hogging my cpu to an alarming extent (~60%!) so I uninstalled it and installed alsa instead. The machine isn't going to break any speed records, but everything is running smoothly now.

---

