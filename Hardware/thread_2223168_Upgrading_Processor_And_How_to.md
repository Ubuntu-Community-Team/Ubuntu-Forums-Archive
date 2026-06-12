---
title: "Upgrading Processor? And How to"
date: 2014-05-09
forum: Hardware
---

### Post by beenny on 2014-05-09
Hello All,

I bought a Dell XPS desktop 3 years ago when they were selling them with Ubuntu pre-installed. I've noticed over the past year or so things have gotten pretty laggy whenever I try to do any multitasking and particularly when switching between users. This is primarily an internet/word processing computer for me an my wife. Any real computing I VPN int my work computer so don't think I need anything that major. Though there may be a lot of tabs open at any given time.

It is currently has an AMD Athlon II  X4 630 Processor with 4gb of RAM. Should I look to upgrade the processor, RAM or both? What would be recommended? All my other computers have intel and i've had no problems so I'm not sure this is an AMD thing so do I need to stay in that family or can I move to an intel processor?

Also I have never done this before - and am excited to learn - so some newbie steps would be great...

Thanks,

Ben

---

### Post by Tadaen_Sylvermane on 2014-05-09
It is very easy to change out parts on a computer. For a switch to Intel you need a motherboard as well. 

I'm thinking something else is wrong with your computer other than the cpu & ram. Those are more than enough for Ubuntu, even the latest LTS. I think an SSD would fix you right up personally.

---

### Post by beenny on 2014-05-09
Thanks for the reply.  I figured I had to stay with AMD - which is fine.

I don't think it's just the video card b/c I do notice the load monitor gets pretty maxed out at times. Though the video card is:

AMD/ATI RS880 Radeon HD 4200

I can see spending up to $200/$300 if this will extend the life of the computer - though obviously less is better. After that it seems like it is just worth getting something completely new.

I'm also wondering if this could just be an Ubuntu thing and if it makes trying out a Mint or some other distro. I've heard memory management hasn't been the best since Unity...

bg

---

### Post by beenny on 2014-05-09
A SSD for home desktop seems like a bit of overkill doesn't it? My other computers without SSD have never had this problem. Is it possible that a clean install of Ubuntu would solve some of this? I just upgraded to 14.04 but tend to be lazy and just upgrade through the download manager...

---

### Post by mörgæs on 2014-05-09
This is powerful gear and I don't see a need for buying more. 
Yes, experimenting with fresh installs is the way to go. Also X/Lubuntu might be interesting.

---

### Post by beenny on 2014-05-09
That's an interesting thought. Is there anything lost by going to lubuntu or xubuntu? While this isn't my workhorse computer I will occasionally run some computational jobs (i'm a computational statistician) and my wife will want to edit photo or videos.

---

### Post by mörgæs on 2014-05-09
Nothing lost. 
One can run the same applications just with less overhead due to a greedy desktop environment.

---

### Post by gordintoronto on 2014-05-10
As to the original question, the answer is no. That CPU fits in an AM3 socket, and the only CPU for AM3 currently available on Newegg is single-core. You might find a used Athlon II X4 650, which runs at 3.2 gHz versus the 2.8 of your current processor. Not much gain.

Do you track your memory usage? "Lots of tabs" means different things to different people; 40 tabs, with videos in a few of them, will bring most systems to their knees.

It might also be the hard drive. Is it healthy?

---

### Post by Bashing-om on 2014-05-10
beenny; Hello,

Here might be the bottle - neck.
> 
AMD/ATI RS880 Radeon HD 4200

3 years ago, that was a good card - however, with no vendor support, gets into a grey zone .
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)


Which means a restriction is in effect that open source drivers should be used for the graphics, else there will be problems.
To check:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```

Want better graphics,
[INDENT][INDENT][INDENT]get a better graphics card -> cost wise, the sky is the limit[/INDENT][/INDENT][/INDENT]

---

### Post by beenny on 2014-05-10
Thanks all for the replies.

The hard drive seems like it's fine in the sense that there is a lot of space still on it. As for "lots of tabs" no it really isn't even 40 - more like 10-20 without video - i have flash blocker on chrome so videos won't play automatically.

As for the graphics card:

```

[Sat May 10 ~]$lspci -nnk | grep -iA3 vga
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880 [Radeon HD 4200] [1002:9710]
	Subsystem: Dell Device [1028:0458]
	Kernel driver in use: radeon
01:05.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RS880 HDMI Audio [Radeon HD 4200 Series] [1002:970f]

```

```

[Sat May 10 ~]$sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: RS880 [Radeon HD 4200]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:e000(size=256) memory:fe9f0000-fe9fffff memory:fea00000-feafffff

```

Not sure hwo to interpret the output - but does this indicate it could be the card? I don't really want to go about reinstalling Ubuntu or lubuntu if it is not likely to solve anything...

One other thing - I have noticed that everything is a bit more laggy on my side than my wife's side. I definitely have more programs installed so maybe that does speak to a clean install?

---

### Post by Yellow Pasque on 2014-05-10
Have you checked memory usage when things slow down?
```
free -m
```

> Not sure how to interpret the output
It's fine.

>  I don't really want to go about reinstalling Ubuntu or lubuntu if it is not likely to solve anything...
You don't have to reinstall. You can test a LiveUSB to see if the same behavior occurs there.

---

### Post by beenny on 2014-05-12
Yeah things do seem smoother with the LiveUSB - I suppose a reinstall it is. 

The funny thing is, I must have gotten used to Unity b/c I found lubuntu kind of ugly looking! Is there a way to reduce the overhead on unity/ubuntu or make lubuntu a little prettier. I kind of like the dash...

---

### Post by mörgæs on 2014-05-12
Again, your hardware is strong and I'm not sure that you need tweaking. How does a fresh install of Ubuntu 14.04 behave?

---

