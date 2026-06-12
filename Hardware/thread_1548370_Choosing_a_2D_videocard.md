---
title: "Choosing a 2D videocard"
date: 2010-08-08
forum: Hardware
---

### Post by ozzynotwood on 2010-08-08
[B][FONT=Arial][SIZE=2]Hello Everyone, this is my first post. I've been using windows since v3.1 and I am going to order a new PC and start using ubuntu. Based on my research, upgrading to ubuntu will make you all cheer and there will be group hugs all around, am I right? lol

Anyway, I'm having an impossible time choosing the right video card, I dont play games, not even solitaire, so I just need something that will give me excellent 2D performance access two 24inch monitors.

The relevant parts I've chosen are:
Gigabyte GA-H57M-USB3
i7 875K CPU
6gb RAM
x2 160gb hdd running RAID 0

I will be doing music production, and I do like a fast responsive computer when I'm multitasking across my 2 screens. I also watch DVD's and alot of youtube. There is also alot of visual things happening within music software.

Based on my reseach:

1. ATI cards are hell to install on ubuntu and don't perform well[/SIZE][/FONT][/B][SIZE=2], **so dont even bother.**
[B]
2. A 'Toms hardware review" benchmark showed better video performance from an on-board video from a 2008 motherboard[/B][/SIZE]

**[SIZE=2]3. When asking for advice, the usual response is "Well I have THIS, so you should get one, its great"[/SIZE]**
[B]
[SIZE=2]4. I've heard that using a 3D accelerated card on a 3D desktop is faster than running a 2D desktop on the 2D side of a video card, is there any truth to this?[/SIZE][/B]

**[SIZE=2]I hear the ubuntu community is full of 'tweakers' so I'd greatly appreciate some answers on my questions, thanks guys![/SIZE]**

---

### Post by S.R on 2010-08-08
I would start out with researching what GPU's plays well with the motherboard you have selected. Then pick from that grouping and get everyone's two cents worth.

Contrary to the assumption I have dual ATI 5770's on my custom rig. The drivers were not as easy as plug-n-play but they were not a burden to install.

---

### Post by cascade9 on 2010-08-08
ATI cards arent that bad. They will work, just they are slightly more likely to have problems with the drivers. 

For watching youtube, they wont be any difference between any of teh modern video cards (not hardware acceleration for flash under linux). As for DVDs and downloaded videos- VDPAU (nVidia hardware video decoding) is a nice thing, it does lower the CPU use when watching supported video formats a lot. 

Probably your best bet would be a nVidia GT220. 

BTW, 2 things I have to ask- 

6GB of RAM? That is normally a LGA 1366 (triple channel RAM i7) amount of RAM (3x2GB). Its more than possible to run 2x2GB and 2x1GB RAM in a LGA 1166 motherobard, is that what you are doing? 

2x 160GB HDs in RAID 0? You are aware that if one drive fails, yuo will lose all your data, right? Its not worth it for speed really. Sure, RAID 0 is faster than a single drive, but a more modern HDD coul possible pass the speeds of RAID 0 on old, or low, density drives. IMO you would be much better off with a single 1TB 7200 HDD or better yet, an SSD + 1 or 2 HDDs.

---

### Post by PresenceofMind on 2010-08-08
> **ozzynotwood said:**
> [B][FONT=Arial][SIZE=2]Hello Everyone, this is my first post. I've been using windows since v3.1 and I am going to order a new PC and start using ubuntu. Based on my research, upgrading to ubuntu will make you all cheer and there will be group hugs all around, am I right? lol

Anyway, I'm having an impossible time choosing the right video card, I dont play games, not even solitaire, so I just need something that will give me excellent 2D performance access two 24inch monitors.

The relevant parts I've chosen are:
Gigabyte GA-H57M-USB3
i7 875K CPU
6gb RAM
x2 160gb hdd running RAID 0

I will be doing music production, and I do like a fast responsive computer when I'm multitasking across my 2 screens. I also watch DVD's and alot of youtube. There is also alot of visual things happening within music software.

Based on my reseach:

1. ATI cards are hell to install on ubuntu and don't perform well[/SIZE][/FONT][/B][SIZE=2], **so dont even bother.**
[B]
2. A 'Toms hardware review" benchmark showed better video performance from an on-board video from a 2008 motherboard[/B][/SIZE]

**[SIZE=2]3. When asking for advice, the usual response is "Well I have THIS, so you should get one, its great"[/SIZE]**
[B]
[SIZE=2]4. I've heard that using a 3D accelerated card on a 3D desktop is faster than running a 2D desktop on the 2D side of a video card, is there any truth to this?[/SIZE][/B]

**[SIZE=2]I hear the ubuntu community is full of 'tweakers' so I'd greatly appreciate some answers on my questions, thanks guys![/SIZE]**

Hello :D

I haven't heard anyone talk about 2D graphics card for a loooong time. Besides why settle for 2D when you can have 3D :P

As far as running two-monitors go, you really only need a single graphics card that has at least two monitor ports rounds its back. Else two graphics cards are needed and you have to go SLi or Crossfire depending on your choice.......

Things like Nvidia 220 GT or ATi 4850 will do quite nicely (most of the modern graphics cards will do the job anyway...pick one that suits your budget)

Everything else looks alright to me.....unless you want extra performance enhancements from those components.

---

### Post by ozzynotwood on 2010-08-09
Thanks for the replies guys, I'll be using the knowledge tonight's shopping of parts.

Just wanted to answer the question about having 6gb of RAM. I do music production with large wav files and VST's. I also want to use windows 7 on virtualbox, so i thought I'd allocate 3gb of ram to each, do you think this will be enough?

Thanks again!

---

### Post by PresenceofMind on 2010-08-09
> **ozzynotwood said:**
> Thanks for the replies guys, I'll be using the knowledge tonight's shopping of parts.

Just wanted to answer the question about having 6gb of RAM. I do music production with large wav files and VST's. I also want to use windows 7 on virtualbox, so i thought I'd allocate 3gb of ram to each, do you think this will be enough?

Thanks again!

I'd settle for 8GB (4 x 2GB). That way you can get a full dual-channel system running, which will do good on the motherboard that you have picked as this will have both the speed and capacity. But if you would like more of capacity than speed then your current configuration will make it.

---

### Post by cascade9 on 2010-08-09
3GB each should be tons. Even 2GB each would work well. 

> **PresenceofMind said:**
> I'd settle for 8GB (4 x 2GB). That way you can get a full dual-channel system running, which will do good on the motherboard that you have picked as this will have both the speed and capacity. But if you would like more of capacity than speed then your current configuration will make it.

Better to have 4GB x2 than 2GB x 4. More room for future upgrades, less chance of issues (not much chnace of there being issues with 4 sticks of RAM if you arent overclocking, but it can happen). 

6GB in dual channel is totally possible as well, 2 x 2GB + 2 x 1GB.

---

### Post by PresenceofMind on 2010-08-09
Great, so pick on that suits the budget........ 2 x 4GB or 4 x 2GB. 

> More room for future upgrades, less chance of issues 

I don't know what issues you can encounter for using up all your RAM slots... and there are a lot of ways to upgrade whatever method you choose.... as long as it fits the budget.

Heck, I don't even know if any overclocking is needed here or if ozynotwood wants what dual channel setup has to offer. With the spec he's got at the moment, he's in for a nice PC.

> 6GB in dual channel is totally possible as well, 2 x 2GB + 2 x 1GB.I'd still go for 8GB.....just because 8GB is more than 6GB lol

---

### Post by cascade9 on 2010-08-09
> **PresenceofMind said:**
> I don't know what issues you can encounter for using up all your RAM slots... and there are a lot of ways to upgrade whatever method you choose.... as long as it fits the budget.

Apart from some motherboards that have 'known issues' with 4 slots being filled (IIRC the i650 chipset had this with the original BIOS versions),  4 RAM slots filled is more likely to have stability problems. Not that many people would have this happen (1 in a 100 would be pessimistic) but it can happen. Normally the only people who notice this are heavy overclockers. ;)

---

### Post by PresenceofMind on 2010-08-09
> **cascade9 said:**
> Apart from some motherboards that have 'known issues' with 4 slots being filled (IIRC the i650 chipset had this with the original BIOS versions),  4 RAM slots filled is more likely to have stability problems. Not that many people would have this happen (1 in a 100 would be pessimistic) but it can happen. Normally the only people who notice this are heavy overclockers. ;)

ok.... i'll take your word for it. I guess I'd have to do some research and find out what these 'issues' are myself.

---

