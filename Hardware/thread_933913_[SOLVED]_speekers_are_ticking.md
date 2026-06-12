---
title: "[SOLVED] speekers are ticking"
date: 2008-09-29
forum: Hardware
---

### Post by ChanServ on 2008-09-29
they just keep going tickticktickticktick really fast, it has nothing to do with ubuntu, but is there ayway i can fix it withough haveting to replace them?

EDIT: dammit i misspelled speakers :|

---

### Post by Crafty Kisses on 2008-09-29
What is the result of this command?
```
lspci
```

---

### Post by anystupidname on 2008-09-29
Get outta there! They're gonna blow!

---

### Post by ChanServ on 2008-09-29
> **Codename said:**
> What is the result of this command?
```
lspci
```
```
00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Device 05b1 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)
04:00.0 VGA compatible controller: nVidia Corporation Device 0614 (rev a2)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

```
but i know it has nothing to do with ubutnu. so that is kind of rendered useless
> **anystupidname said:**
> Get outta there! They're gonna blow!
OH SHI- 

 :p

---

### Post by mtbsoft on 2008-09-30
You seem sure it has nothing to do with Ubuntu... how have you reached this conclusion?  Oh and some more hardware details wouldn't go amiss either.



p.s. BOOM!

---

### Post by ChanServ on 2008-09-30
> **mtbsoft said:**
> You seem sure it has nothing to do with Ubuntu... how have you reached this conclusion?  Oh and some more hardware details wouldn't go amiss either.



p.s. BOOM!

well for starters it happens when i dont have my computer on. that kinda proves it :p

anyway, the mobo is a evga 790i with a core 2duo ( 3.2GHz ) and I have one 8800gts and one 9800gt in sli ( yes i know your not suppost to sli them ). if that helps at all....

---

### Post by markbuntu on 2008-09-30
I think I read something about that in this file or one near it:

/user/share/doc/alsa-base/driver/ALSA-Configuration.tar.gz

---

### Post by mtbsoft on 2008-09-30
> **ChanServ said:**
> well for starters it happens when i dont have my computer on. that kinda proves it
In which case some hardware info. about the speakers might have been more relevant, don't you think?  What make/model?  How are they connected and to what?  Does it happen when they are just connected to the power source?  Internal power supply or external?  C'mon, provide some relevant information if you want serious help.

---

### Post by lisati on 2008-09-30
> **ChanServ said:**
> well for starters it happens when i dont have my computer on. that kinda proves it :p



Sounds like your speakers are picking up some interference from somewhere. Possibilities include a capacitor in their power supply needing replacement.....

---

### Post by ChanServ on 2008-10-01
> **mtbsoft said:**
> In which case some hardware info. about the speakers might have been more relevant, don't you think?  What make/model?  How are they connected and to what?  Does it happen when they are just connected to the power source?  Internal power supply or external?  C'mon, provide some relevant information if you want serious help.

I have actualy almost no information on the speakers at all, i know that they used to be in a silver case, thats about all :\. 

Anyway, i was moving them out today, and accidently droped them, they sound a lot better now, a wire or two must have been toutching.

---

