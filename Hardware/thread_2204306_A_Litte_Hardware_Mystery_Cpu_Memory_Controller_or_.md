---
title: "A Litte Hardware Mystery: Cpu Memory Controller or Bad Bios?"
date: 2014-02-07
forum: Hardware
---

### Post by magaudio on 2014-02-07
[COLOR=#070F14][FONT=Verdana]So guys,[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]I have a system (s15c durabook laptop i5 cpu w/ built in memory controller in cpu) that is a bit wonky. Basically it will randomly freeze. No error codes/blue screens it just freezes. It has problems with memory intensive tasks. CPU/GPU stress tess: no problem really. Run a memory test or start loading a bunch of pages/programs and it freezes.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]When I first got the system it would fail pretty much right after boot. It would start to load OS/read from CD and then just give a blinking cursor. I noticed that if I did a "reset bios to defaults" it would go a while longer...like five to ten minutes of actually running. If I do a reset a couple times in a row (reset, wait till loading, turn off, reset, etc.) it lasts a lot longer! **>>this system does not reboot after bios change...it leaves bios setup and immediately starts loading sequence after as if It is writing changes to ROM and the Bios instructions loaded in memory and continuing on. <<[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]It really started going for a long time like 20-30 minutes once I removed the cpu and reseated it.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]It has 2 sticks of ram --- both sticks by themselves cause memtest to freeze (countdown stops, no error, little red cross still blinks). Together the failure occurs faster. because of other factors having huge effects like reseating processor and bios resets I dont think its ram.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]Loading a bios flash utility to make a ROM copy causes failure instantly--program doesn't even run.[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]It seems to me that the system BIOS is actually fine because I can run the system for up to 25 minutes and use all of the systems hardware. ***This would make me think that the instructions that the bios is loading into memory are good!*** Its the memory link between bios and ram that is bad.[/FONT][/COLOR]


[COLOR=#070F14][FONT=Verdana]My thoughts are that the CPU memory controller has been damaged by being improperly seated for a long time. Once I reseated the CPU things really improved altogether, but I think that the CPU[/FONT][/COLOR]
[COLOR=#070F14][FONT=Verdana]memory controller has been made unstable. It gets the instructions from the BIOS and loads them to memory but somewhere down the line it fails....and it fails even more when you try to access the bios outside of the standard bios utility. (using a dos or windows flash utility...dont worry I was just trying to copy the current bios not flash in windows.)[/FONT][/COLOR]

[COLOR=#070F14][FONT=Verdana]What do you guys think? [/FONT][/COLOR]

---

