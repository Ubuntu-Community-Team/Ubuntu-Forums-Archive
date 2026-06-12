---
title: "Some problems I suspect i'm having with my drivers."
date: 2015-11-09
forum: Hardware
---

### Post by immanuel3 on 2015-11-09
Hi,
I have been using Ubuntu for about three mounts now. 
And the only problem I seem to be having is with my GPU and setting up my nvidia drivers.
I will break my problem down so it will be easier to address every point.
Specs:
GPU: GeForce GTX 970
CPU: i7-4790K
OS: Ubuntu 14.04 LTS 64-bit

1) _What driver should I use? and what version is the latest?_
Currently under: "Additional drivers" in the software&Updates tab I am using this driver: NVIDIA binary driver - version 346.96 from nvidia-346 (proprietary,tested).
But when going to the nvidia web site the latest version is: [COLOR=#000000][FONT=Trebuchet MS]352.55 ([https://www.nvidia.com/download/driverResults.aspx/92826/en-us](https://www.nvidia.com/download/driverResults.aspx/92826/en-us)[/FONT][/COLOR]).
Why do I not have the latest version? 

2) [U]Why is my GPU Unknown?
[/U]This appears:
[https://i.imgur.com/nHeDXoh.png](https://i.imgur.com/nHeDXoh.png)
But when I look at my: "About this computer" tab is see under graphics: GeForce GTX 970/PCIe/SSE2.
Why is this happening ?
Is that conman or is it some kind of problem?

Are these actual problems or am I just misunderstanding something?
Thank you!

---

### Post by weatherman2 on 2015-11-09
> **immanuel3 said:**
> 

1) _What driver should I use? and what version is the latest?_
Currently under: "Additional drivers" in the software&Updates tab I am using this driver: NVIDIA binary driver - version 346.96 from nvidia-346 (proprietary,tested).
But when going to the nvidia web site the latest version is: [COLOR=#000000][FONT=Trebuchet MS]352.55 ([https://www.nvidia.com/download/driverResults.aspx/92826/en-us](https://www.nvidia.com/download/driverResults.aspx/92826/en-us)[/FONT][/COLOR]).
Why do I not have the latest version? 


NVidia updates their Linux drivers now and then and releases them to the Linux community.  But just releasing a new driver doesn't mean it's automatically compatible with Ubuntu or with whatever version of Ubuntu you are using.  The driver must be tested to make sure it will "build" with your version of Ubuntu and also doesn't cause bugs with that version, etc.  Someone has to do that process - doesn't happen automatically.

You aren't required to use Ubuntu's "additional drivers" feature to install drivers, FYI.  But it's easier and safer that way. You could, if you desired, download the latest driver source code (or even a Debian or Ubuntu package) from Nvidia directly and build it yourself.  Maybe it would work fine; maybe it won't even build without errors or maybe it will be a big hassle to get it to build correctly.

And in the end, even if you could compile the driver yourself, it may not make any difference at all.  If there are no specific bugs with your graphics card that cause you grief, there is no reason at all to update the driver - just leave it alone.

I can't answer the second question "Why is my GPU Unknown" but again, unless you are having some problems with graphics, I would't worry about it.

---

### Post by immanuel3 on 2015-11-09
The reason i'm looking in to this is because Blender wont recognize my GPU. And I was thinking it might be because my drivers are out of date.
Thank you for the reply !

---

### Post by weatherman2 on 2015-11-09
Sorry, I don't know what Blender is.  Is it causing you some issue?  Slow performance?

---

### Post by tokyobadger on 2015-11-10
Most recent stable driver supporting your card is 352.55 2015/10/14
Newest stable driver supporting your card is 355.11 2015/08/31
Newest beta driver supporting your card is 358.09 2015/10/12

Why don't you have them? Because the Ubuntu package maintainers have not included them and considering that you're using an 14.04-LTS release chances of seeing 35x.yy or later drivers are slim to nil.

However, Ubuntu did initiate a semi-official ppa recently that combined the work of the xorg-edgers and mmarley ppa's - [more info here]("https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa") - adding the ppa to your repos gives you access to newer drivers. Caveat emptor - they are not fully official or supported. I'm using 358.09 with GTX680 on 15.10, 16.04, and a couple of debian derivatives as well as debian sid without issue.

What should you use? Whatever works best for you would be my answer. With a ppa you assume some level of risk but get access to newer drivers.

Why is the card "unknown"? Couldn't say - maybe the Sept 2014 release date was after the April 2014 release date and there is some form of "internal card database" for the additional drivers. My GTX680 is recognized.

Why does about this computer identify it? Probably scrapes something like lspci | grep VGA? <-- doesn't look like lspci ...

When you open nvidia-settings is your card and driver version correctly identified?

If so, you have no problems

**edit:** the GPU info comes from glxinfo (about this computer is the system tab data from the old gnome-system-monitor - rest remains in system monitor - so I guess this app pulls from glxinfo)
```
OpenGL renderer string: GeForce GTX 680/PCIe/SSE2
```

**edit2:** for blender on Linux with nvidia it seems you need to run as root at least one time to enable the GPU for use by blender (your device is definitely supported). [see here for more info](http://blender.stackexchange.com/questions/7485/enabling-gpu-rendering-for-cycles)

---

