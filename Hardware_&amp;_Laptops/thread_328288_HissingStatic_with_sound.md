---
title: "Hissing/Static with sound"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by neocookie on 2006-12-30
I'm having problems with the sound on my laptop. I'm getting an irritating hissing/static/white-noise from the soundcard, whether via speakers or earphones. I've tried switching sound from alsa to esd in "System > Preference > Sound", but it doesn't seem to have helped.

I'm not sure what soundcard I have, as its integrated and I wouldn't know how to find out through linux.

I've searched through the forums already, and have tried a few different things, but with no luck. Can anyone help me track down the issue, or give me pointers on where I can start?

---

### Post by lloyd_b on 2006-12-30
First step: Find out what sound card you're using.

Run the command "lshw", and look through the output for a device listed as "multimedia audio controller" or something similiar.

Lloyd B.

---

### Post by neocookie on 2006-12-31
Perfect! This is what I got back:

*-multimedia
description: Multimedia audio controller
product: IXP SB400 AC'97 Audio Controller
vendor: ATI Technologies Inc
physical id: 14.5
bus info: pci@00:14.5
version: 80
width: 32 bits
clock: 66MHz
capabilities: bus_master cap_list
configuration: driver=ATI IXP AC97 controller

From that I'm guessing its an "ATI IXP SB400 AC97" card.

How do I go about tracking down and resolving the hiss now? :)

---

### Post by earobinson on 2007-01-14
I have the same problem 
multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:dddf8000-dddfbfff irq:50

---

### Post by Ecthelion on 2007-02-13
I also have this problem...

 *-multimedia
             description: Audio device
             product: High Definition Audio/AC'97 Host Controller
             vendor: ALi Corporation
             physical id: 14
             bus info: pci@00:14.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:d7fd4000-d7fd7fff irq:98

---

### Post by Ecthelion on 2007-02-13
Lol I was able to solve this problem 3 minutes after my previous post...

I installed **alsamixergui** and put the volume for the "Line" on the maximum.
The hiising noise dissapeared and everything else still works fine.

So maybe this can help you guys too :-)

---

### Post by hotani on 2007-03-23
I have a similar problem, it seems the speakers are playing what is going on inside the computer. For example, if it is accessing the HD, I get a bunch of static. Moving the line switch all the way up did not help--it actually made it worse. :(

My soundcard is a HDA NVidia with a Realtek ALC883 chip according to the alsamixergui.

---

### Post by kolslorr on 2007-04-07
Same problem. 

Definitely desperate for a solution.

---

### Post by hotani on 2007-04-07
This static is present on all my machines, and fortunately, since it is coming out soon, the one running Feisty is the quietest. On that box, it is just a faint clicking sound I only hear through the headphones. Edgy machines are full of static. Not sure if that has something to do with the OS or not.

---

### Post by fearpi on 2007-12-27
I have this same issue. I have had it for a long time, since at least as far back as Dapper. Feisty was the quietest, but I think Gutsy might be the worst so far. I have:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Any end-all cure yet?

---

### Post by earobinson on 2007-12-31
one of the ways you can fix this is to turn down the PCM volume (right click the volume icon then click open volume controle)

or run "gnome-volume-control" in the terminal

---

### Post by gunashekar on 2007-12-31
just to say me too.
Same problem here on one of my machines but only since I started playing with Hardy builds. On my computers with Gutsy I have no problem with my desktop but have no sound on my laptop (HDA Intel ICH 7) .

---

### Post by fearpi on 2007-12-31
> **earobinson said:**
> one of the ways you can fix this is to turn down the PCM volume (right click the volume icon then click open volume controle)

or run "gnome-volume-control" in the terminal

This presents a problem when PCM is the ONLY working volume control.

---

### Post by bigpimpatl on 2008-06-20
changing the PCM volume totally fixed the problem for me! thanks! :guitar:


i was getting so frustrated how to fix this problem

---

### Post by ksbalaji on 2008-06-26
> **hotani said:**
> This static is present on all my machines, and fortunately, since it is coming out soon, the one running Feisty is the quietest. On that box, it is just a faint clicking sound I only hear through the headphones. Edgy machines are full of static. Not sure if that has something to do with the OS or not.

I have
ATI IXP SB4x0 High Definition Audio Controller
I have the same problem. I find that the high pitch sound like something in a fax machine comes when computer accesses HD or when the mouse is moved.
It is not OS dependent. My XP does not have the problem.  Even Ubuntu was OK until recently when I tinkered with alsa and EnhancedSound and XMMS2. I also feel that something in sound config has to be changed.

---

### Post by kwirk on 2008-06-26
I fixed the hissing by muting the 'Line-In', 'CD' and 'PC Speaker'. Each one seemed to add a little more volume to the hiss, and was only solved by muting all 3. I've had this problem since Edgy, with no problem present in Windows XP.

If anyone is interested:
Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

---

