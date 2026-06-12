---
title: "Is the Intel open source drivers for the Intel graphics any good?"
date: 2008-09-30
forum: Hardware
---

### Post by castlefox on 2008-09-30
Is the Intel open source drivers for the Intel graphics any good?

I want to help support hardware that has open source drivers.

I want to know how they work to play video games such Doom3 and other video games.

---

### Post by MusicMastaMike on 2008-09-30
I'm not a gamer, so I'm not sure about any of that.  I've never had any problems running desktop effects of anything of the sort, though.  I'm using a 945GM chipset and the default video driver installed by Ubuntu (i8xx/i9xx).

---

### Post by L815 on 2008-09-30
I also have the intelgm965 card and with Intrepid, video works well with compiz. The only thing I've noticed is the effects aren't as smooth when there are big windows open, and there is a wave once and a while that shows when playing video full screen (looks like a refresh)

---

### Post by reacocard on 2008-09-30
The intel drivers are some of the best in linux, IMO. I have both a 915GM and an X3100, both of which have worked absolutely perfectly under linux.  For a while, the X3100 linux drivers were actually better than the vista ones. They still might be for all I know. :D

---

### Post by castlefox on 2008-09-30
> **reacocard said:**
> The intel drivers are some of the best in linux, IMO. I have both a 915GM and an X3100, both of which have worked absolutely perfectly under linux.  For a while, the X3100 linux drivers were actually better than the vista ones. They still might be for all I know. :D

Well that is very good to hear that they are working well for you guys.  

I still would like to see how the X3100 does in some 3d games.  I dont want to throw away my PC gaming habits just yet

---

### Post by WhiteHorse on 2008-10-24
I used the intel driver from the Ubuntu repos. I get about 15fps in Nexuiz and 600fps in glxgears. Most 3D games are barely playable, even at a low res with no effects.

---

### Post by reacocard on 2008-10-24
> **WhiteHorse said:**
> I used the intel driver from the Ubuntu repos. I get about 15fps in Nexuiz and 600fps in glxgears. Most 3D games are barely playable, even at a low res with no effects.

That's just because intel cards aren't exactly powerful. Until the X3100 they didn't even have support for modern graphics features such as hardware transform and lighting, so cards prior to those will of course get worse performance in games. The reason some games are playable in windows on these cards is usually because directx cuts some corners in the rendering in order to boost framerate. Linux's OpenGL implementation doesn't do this.

FWIW I can play nexuiz, quake and warsow wonderfully on my X3100 with no lag or tearing at all. I haven't experimented with more-advanced games but I expect the results would be similar, just don't expect to play at the highest quality or resolution. Trying to play any games under wine however is a slideshow.

---

### Post by Potters Son on 2008-11-12
Hi. I have an HP dv6985se laptop with a GM965 graphics card, and my computer isn't using it. I'm running 8.10 32-bit edition. Currently, I'm using the VESA driver (which gets me the resolution I want, but no hardware acceleration). I've tried to select the i810 driver from displayconfig-gtk, but it fails when I click the [test] button. I'm scared of putting a 'driver "intel"' section into my xorg.config file, because I read some other threads by people who did that, and their graphics wouldn't work. I have the xserver-xorg-video-intel package installed.

Could anyone give me advice? Like, which driver should I try and use?

Thanks in advance for any help.

---

### Post by reacocard on 2008-11-13
> **Potters Son said:**
> Hi. I have an HP dv6985se laptop with a GM965 graphics card, and my computer isn't using it. I'm running 8.10 32-bit edition. Currently, I'm using the VESA driver (which gets me the resolution I want, but no hardware acceleration). I've tried to select the i810 driver from displayconfig-gtk, but it fails when I click the [test] button. I'm scared of putting a 'driver "intel"' section into my xorg.config file, because I read some other threads by people who did that, and their graphics wouldn't work. I have the xserver-xorg-video-intel package installed.

Could anyone give me advice? Like, which driver should I try and use?

Thanks in advance for any help.

run the intel one. Seriously, -intel has been stable for a long time now. Sure when it first became available it was a little flaky, but it's been solid for the last couple releases. I've run it with my 965 for nearly a year with no issues, and with a 915 for another year-ish before that.

---

### Post by Potters Son on 2008-11-14
Okay. I inserted 'display "intel"' into xorg.conf, so the section of that file reads,
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"intel"
EndSection

```

Still, I run top in a terminal, and the most intensive process is xorg, hanging anywhere between 10-20%. Compiz lags on my laptop, but it shouldn't; I have a 64-bit Centrino processor with 4 gigs of RAM.

How can I tell if my computer really is using the intel driver?

Thanks

---

### Post by Twitch6000 on 2008-11-14
Well I know the intel card I have on my old laptop(intel 945) works great with 2d game and some basic 3d games(you know ones that are very light on the machine).

I was able to run these games real well no problem on the laptop(acer aspire 9410).

Starcraft Broodwar

Red Alert 2

Warcraft 3

Frozen Bubble 2(hey you knew I was going to mention it :p)

Alien Arena(however the FPS jumped alot)

So yeah... I would say Intel cards are only good for 2d games and maybe basic 3d games.

---

