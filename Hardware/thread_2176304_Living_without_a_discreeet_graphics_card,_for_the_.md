---
title: "Living without a discreeet graphics card, for the time being?"
date: 2013-09-23
forum: Hardware
---

### Post by Proinsias on 2013-09-23
Hi all, 

I've been playing around with linux for a few years on various old desktops, laptops and occasionally running it on ppc and intel macs. 

Whislt I've been loving it and learning lots I'm thinking it's time to go full time linux and install it on something that isn't old, sad & full of compromise. I want to build something new and shiny that I can build up over time. It's been about 20 years since I last built a computer, at that point I was 11 & relied on the advice of a friend and one or two PC magazines, after a week or two of looking into it seems there is a little more info easily accesible on this sort of thing than there was in 1993, to the point of sensory overload,

At the moment I'm thinking:

Full size case, around $100 or so, Coolermaster is looking good
SSD drive ~60-120GB for everything that isn't /home or media - I've got a few old sata drives for bulk storage
Intel i5, not sure which - hence the post
Motherboard - not sure either veering towards gigabyte/asus in the $150 range
1x8GB Corsair/Crucial RAM to get started, would like a mother board to support 4 of them with the march of time.

This is a my first rough sketch and everything is up for debate - well maybe not everything, I think I'm sold on ssd for the root partition at least.

Optical drives, display, hard disk storage, decent gaming, pci etc are all things I can live without but will add in as quality devices when I have the cash - I want a solid, fast, base system first.

What I was wanting to find out about is the sort of graphics performace I can expect from an Intel i5 without any additional graphics card. I was hoping I could get by the coming months or even year whilst I save up for a decent graphics card. My gaming needs are effectively zero for that period, I can get by with mame or dosbox. What I'm concerned about is spending several hundred pounds on something that can't handle 1080p video as well as my Raspberry Pi. My needs I think are fairly modest to start off, but I want something that will play any video I throw at it and is ripe for expansion.

I'd rather not buy a dirt cheap graphics card to get me by but will do if I need to. 

Thoughts?

---

### Post by ajgreeny on 2013-09-23
I have an Intel i5-3570K on an ASUS m/b (can't remember the exact number), 8GB ram and no separate graphic card, so I depend entirely on the Intel HD4000 graphics.  It is brilliant; much better than I expected, so I would think you'll have no problems at all.

I am not a gamer, but I do a bit of video work, both watching and editing with no problems at all using the integrated GPU.

---

### Post by bibek2 on 2013-09-23
> **ajgreeny said:**
> I have an Intel i5-3570K on an ASUS m/b (can't remember the exact number), 8GB ram and no separate graphic card, so I depend entirely on the Intel HD4000 graphics.  It is brilliant; much better than I expected, so I would think you'll have no problems at all.

I am not a gamer, but I do a bit of video work, both watching and editing with no problems at all using the integrated GPU.

Intel HD4000 is an excellent graphics card. The only problem with Intel graphics card is that the linux driver does not support Opengl Version greater than 3.2 (or 3.1). A lot of Macbooks too use this graphics card.

---

### Post by Proinsias on 2013-09-24
AJ, music to my ears.

Bibek:
This is new territoy for me, could you flesh out, or point me in the direction of, the issues rasied by 3.1/2 and not above compatibility? I'm planning on a discreet graphics card in the future but would rather not hit a brick wall in terms of functionality and be forced into it cheaply and quickly. Not sure if it's relevant but I'm aiming to continue the fairly lightweight setup I'm curently running on a 2005 Advent laptop 512MB RAM, Intel Celeron 1.5ghz: awesome wm, mpd & ncmppcp, luakit, urxvt, mplayer, rtorrent - just to give an idea. 

Thanks for the input, I've done enough reading now to convince me I should do a lot more reading before I break out my wallet,

---

### Post by Yellow Pasque on 2013-09-25
For OpenGL, it depends on what programs you use. A lot of them still use OpenGL 2.1 for compatibility.

As for CPU, I can't think of any reason not to get a Haswell (e.g. i5-4440). They're faster than Ivy Bridge counterparts (CPU and graphics-wise) and they're priced similarly. Just make sure you install buntu 13.10 if you get a Haswell to get the best performance/support for it.

> 1x8GB Corsair/Crucial RAM to get started, would like a mother board to support 4 of them with the march of time.
1. Always use RAM on the mobo vendor's support list (less hassle that way if you run into issues)
2. The benefit of adding large amounts of RAM isn't what it used to be. Unless you're running VM's or doing something else that requires a ton of memory, you'll get more benefit from having two 4GB sticks in dual-channel configuration. If you insist on going the 8GB stick route, bite the bullet and get two now. If you do that, I'm guessing that 16GB will be (way more than) enough RAM for the life of the system.

For the mobo, check out reviews of the Asrock Z87 Extreme4 and Gigabyte GA-Z87X-UD3H. They look like good boards (I've never been an Asus fan myself).

---

### Post by Proinsias on 2013-09-26
Whilst I will be running VM's I don't think I'll be doing any huge leaps beyond what my current half gig of ram allows me on them - just playing around with the nuts and bolts of different linux distro's - I've spent about a year getting Arch installs I enjoy using on my Raspberry Pi & old Advent 7087 laptop. Whilst I want a machine the runs Ubuntu rather well I'm really looking for harware that wil be friendly over years of getting to know the Linux/GNU world. 

 I can aprreciate 2X4GB RAM will perform better than 1X8GB, either should hopefully be more than sufficient for my short term needs, I think I'm going with 8GB as my current needs are modest and my horizon for explansion is MOAR.

Thanks again, any general tips or links for building a desktop I'm hoping to keep as a pet running linux for many years to come would be most welcome.

---

