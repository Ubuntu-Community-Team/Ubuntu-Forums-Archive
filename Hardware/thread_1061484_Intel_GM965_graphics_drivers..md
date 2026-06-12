---
title: "Intel GM965 graphics drivers."
date: 2009-02-05
forum: Hardware
---

### Post by EmanresuusernamE on 2009-02-05
I'm not sure where to start for this, but I was wondering what would be the best way to optimize my Intel GM965 chip set card.  I was poking around my xorg.conf file and noticed that it's almost completely empty, and that it seems like everything is pretty much handled elsewhere in the system.

I know this card is more of a business card, and not really meant to put massive amounts of 3D graphics on the screen, but I'd really like to tweak with it to get the most out of it while on my Ubunto box.  

Where are the graphics settings now located at?  Also, by default is hardware acceleration enabled for Intel chipsets since they have an open sourced driver base?  I tried playing some 3D games, and Wow under wine, and they're very unstable.  I can do everything alright on Windows.

Thanks.

---

### Post by EmanresuusernamE on 2009-02-06
Right, system specs.

Intel Core2 Duo 2.00Ghz, 3G RAM.
Mobile Intel 965 Express Chipset.

---

### Post by David Valentine on 2009-02-12
This is only a partial answer (no tweaking), but this should let you know whether you have graphics acceleration: if ```
$ glxinfo | grep direct
``` yields > direct rendering: Yes you know you're using hardware acceleration (which in this chipset is pretty lame).

Update:  There's quite a lot posted about getting the Intel graphics driver to work better posted on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel").

---

### Post by EmanresuusernamE on 2009-02-13
Thanks, I'll take a look at that site.  I keep trying to do games like Alien Arena, and Wow, and the graphics keep messing up to the point of crashing, or I'll get massive texture errors and I can't tell what's going on at all.

---

### Post by densou on 2009-02-14
> **David Valentine said:**
> which in this chipset is pretty lame

however Intel drivers lacks good performance under Linux compared to Win (mainly, it's related to the too fragmented X structure: Driver+DRI Kernel+MESA+X server) 

it is required a major update for updating 3d rendering performance (kernel+dri module+mesa+driver), a simplier driver update affects 2d only. 

anyway, look at this:
[https://launchpad.net/~intel-gfx-testing/+archive/](https://launchpad.net/~intel-gfx-testing/+archive/)

---

### Post by David Valentine on 2009-02-18
Thanks.  I'm already running the ppa (not edgers) version of the drivers, and am still getting very mediocre performance--tolerable for working, but not nearly as much performance or fun as my nvidia-equipped machine, or as Windows might be on this one.  Your explanation makes sense; I wonder if there's any way to simplify the complex x structure (I hate to see Linux lag behind Windows in any area, but especially in one that so directly affects the user experience).

---

### Post by densou on 2009-02-21
hey lad, I envy you: I want to move in a *cold land of warm hearts* because I can't stand anymore my surrounding shameful place.

well, I don't know if this can affect games but it's an interesting page:
[http://wiki.compiz-fusion.org/Hardware/Intel](http://wiki.compiz-fusion.org/Hardware/Intel)

;)

---

### Post by David Valentine on 2009-02-22
I'm not sure how to use the AIGLX advice because, as I understand it, much of that is now done automagically outside xorg.conf; how does adding options to xorg.conf affect that?  > ...my surrounding shameful placeDon't forget that we have a governor who thinks we should teach "abstinence only" and "creation science" to our kids and that she should be able to ban books.  And she thinks God wants her to be elected President in 2012, and most Alaskans agree.:o

---

### Post by densou on 2009-02-22
> **David Valentine said:**
> I'm not sure how to use the AIGLX advice because, as I understand it, much of that is now done automagically outside xorg.conf; how does adding options to xorg.conf affect that?

it works with this:
[http://spazioinwind.libero.it/densou/xorg.conf.new](http://spazioinwind.libero.it/densou/xorg.conf.new)
puls I suggest to add 
```
agpgart
intel-agp
```
into /etc/modules  {maybe not required anymore to make this trick working because recent kernels should have merged these modules}

> Don't forget that we have a governor who thinks we should teach "abstinence only" and "creation science" to our kids and that she should be able to ban books.  And she thinks God wants her to be elected President in 2012, and most Alaskans agree.

aside political matters, I meant "warm" as "good/honest" while all my fellow-men must be named under "barbarist villains" or worse ;) anyway let's stop this OT chichat here :p (MSN or PM for the continuation)

---

