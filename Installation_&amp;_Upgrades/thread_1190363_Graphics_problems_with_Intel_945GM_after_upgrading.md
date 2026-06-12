---
title: "Graphics problems with Intel 945GM after upgrading to 9.04"
date: 2009-06-17
forum: Installation &amp; Upgrades
---

### Post by philip_bretton on 2009-06-17
Hi 

I upgraded yesterday to 9.04 and everything seemed to work just fine - GUI loaded as usual and I have had no problems until I tried 2 things:
Plugging in a secondary display
And
ctrl+alt+F3 (or any other text based session)

Problem 1:
Plugging in secondary (CRT) screen - no refresh rate higher than 60 - in Hardy I could take the refresh rate up to 85 - why am I going backwards with Jaunty? The screen is unusable at 60 because of flicker.

Problem 2:
ctrl+alt+F3 
And my screen is covered in little white lines, I cannot use the terminal at all.

I think the problems are related (could be wrong) but I think its something to do with the graphics config but I don't know what. I'm not very experienced with Linux and would appreciate any help trying to resolve these.

I looked at my xorg.conf and it just has the following entries (seems a bit simple to me):
```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Before the upgrade it read more like this:
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x768"
		Virtual	1360 1536
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

```

Can someone please help?

Thanks

---

### Post by Racecar56 on 2009-06-17
Intel regressions are in 9.04.

---

### Post by /usr/bin/hacked? on 2009-06-18
> **Racecar56 said:**
> Intel regressions are in 9.04.

Can you explain this a little better please? My 3d graphics, compiz, and high-def playback all go really slowly. I don't have white lines though. Any help would be nice!
Thanks

---

### Post by Mark Phelps on 2009-06-19
It means the Intel drivers are really bad in 9.04.  There are LOTS of posts that mention this.  Intel is "working on the problem" and supposedly, will be producing new drivers.  But the last I saw on this, said they won't be available unti 9.10 comes out.

---

### Post by raymondh on 2009-06-19
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by /usr/bin/hacked? on 2009-06-19
Thanks! Is downgrading to 8.10 possible? I want my high def movies!

---

### Post by raymondh on 2009-06-19
> **/usr/bin/hacked? said:**
> Thanks! Is downgrading to 8.10 possible? I want my high def movies!


Save your personal files someplace else (in the meantime) as you are looking at a clean, fresh, re-install of 8.10.

If you have a separate /home, you could point the installer to overwite the existing / partition whilst NOT REFORMATTING /home.  If it is a "everything-installed-in-root (/)" type of installation, you will defintely overwrite/erase everything when it formats.

AFAIK, there is no network downgrade option. 

Save/back up your files.

Good luck.

---

