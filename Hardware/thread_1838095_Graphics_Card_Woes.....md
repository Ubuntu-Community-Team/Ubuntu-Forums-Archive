---
title: "Graphics Card Woes...."
date: 2011-09-03
forum: Hardware
---

### Post by Scijox on 2011-09-03
I may have made a mistake. I recently purchased a Clevo W150HNQ with the fancy new i7 Sandy bridge processor. I have the new optimus technology. Anyway my installation of xubuntu went pretty smoothly until I tried to install the proprietary nvidia driver. I installed it and did the requisite nvidia-xconfig and it rewrote my xorg.conf as expected. I booted up and... nothing! No displays detected. That was quite depressing. I have been researching the problem for the past 5 hours and I come to find that the linux support for optimus technology is... lacking. It would appear that all video output is routed through my integrated card which stops working once I install the nvidia driver (perhaps someone can correct my if my analysis is unsound).

Ok so I can rm my xorg.conf to resolve the problem but that reverts me back to the opensource driver which doesn't support openGL and leaves me with video tearing and an external moniter with distortions. I also have effectively turned my fancy Geforce 540M video card into a paperweight. I paid a lot of cash for my computer the the thought of turning to windows makes me feel sick (plus I didn't buy it).

I have stumbled across various opensource solutions such as bumblebee and vgaswitcheroo. I got bumblebee to work and I can effectively run programs using optirun and then render in GLX but the performance seems to be lacking. I want a permanent solution. I don't care for optimus technology since it's a load of crap anyway I just want performance. I want my discreet card to run all the time and I want my integrated card to be ignored.

Basically I want my proprietary nvidia driver to work and not result in a blank screen with a "no monitor detected" error. I feel like vgaswitcheroo is the key but I am having trouble getting that to work. I dont care if optimus doesn't work I just want the graphics card that I paid for to work.

Some fourms are telling me that I am simply screwed. I dont have the BIOS option to switch to discreet only so I am in need of some other software fix. If anyone has any advice I would be eternally grateful. I am actually considering switching to windows if I cant fix this (it really REALLY hurts me to do this like I actually would almost rather brand myself with a hot poker).

Any advice would be appreciated

- Scijox

---

### Post by .... on 2011-09-03
> I want my discreet card to run all the time and I want my integrated card to be ignored.You would need a BIOS switch to disable it. I'm not sure if its even possible with recent Optimus because of the way it renders through the IGP. Your best bet is probably ironhide: [http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/](http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/)

---

### Post by Leshrac on 2011-09-03
There's a PPA for ironhide:
[https://launchpad.net/~mj-casalogic/+archive/ironhide/+packages](https://launchpad.net/~mj-casalogic/+archive/ironhide/+packages)

As the previous poster said, it is not possible to disable the integrated card on some of the new models so that's pretty much your only option.

---

### Post by Scijox on 2011-09-03
UPDATE: Basically I managed to get ironhide to work.

When I use optirun glxgears as opposed to glxgears I get much better performance (50 fps vs 500 fps). However, when I use optirun on mplayer I still get noticeable video tearing. This leads me to believe that nvidia's vertical sync is still not working. I also am still having major issues with my external monitor.

I am using xubuntu's default display manager to enable the second display. It enables fine and an image appears HOWEVER everytime I move the mouse or a video is playing the video becomes distortion. The distortion consists of vertical white flickering present across the monitor. Currently, I wish to use my laptop to watch movies and this distortion makes that impossible. The optirun solution is nice but I have to imagine that it doesn't compare to all the features of the wonderful proprietary nVidia driver.

I feel as if the nividia driver (if it would function) would totally solve all these annoying issues but with the crap optimus technology I cant run the nvidia-xconfig without making my computer completely unusable. If anyone has any advice on how I can fix the distortions I would be very grateful. If I cannot fix this issue then I will have to give up on linux for the time being until optimus is supported (if that'll ever happen).

Essentially the bottom line of my rambling is, is it possible, in any way, for me to run the proprietary nVidia drivers AND is there another driver I could consider besides the default that ships with ubuntu (xubuntu)?

---

### Post by .... on 2011-09-03
I think your best course of action for is to wait for Optimus support (or use Windows until then). Intel is making good strides with Sandy Bridge video playback using va-api, but you need to use Ubuntu 11.10 and xorg-edgers PPA to reap the benefits. When you use Linux, you should use ironhide to shut off the nvidia GPU to save battery.

Next time, do research before buying hardware (or buy from a dedicated Linux vendor).

---

### Post by Scijox on 2011-09-03
Yeah I messed up on this one. I cant return it so I guess it's time for windoze :(. I knew optimus would be an issue but I guess I figured the workarounds would work differently than I had hoped. I knew optimus (battery saving ability) would not work but I thought I would have some way to JUST use the discreet GPU. I didn't realize that the video itself was routed through the IGP. I was about 50/50 with this machine and a pangolin performance from system76 :(.

Depressing day. But your comments give me hope that after 11.10 Linux may be a real option for this machine.

One thing that stll gets me though is why am I getting distortions with the default graphics driver on my seconday monitor. It should still be able to use the integrated GPU....

I guess I am going to have to download a fresh copy of windows 7 from Microsoft. :( :( :(

---

