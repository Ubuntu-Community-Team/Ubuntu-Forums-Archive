---
title: "What's this? (pic)"
date: 2008-11-09
forum: Hardware
---

### Post by buccaneere on 2008-11-09
This is my 'resume' screen. Gotta' be related to my shutdown screen distortion...

Any ideas?

Thanks.

---

### Post by phidia on 2008-11-09
That are your hardware specs and what is the version of Ubuntu you're using?

There is a l[aptop testing page]("https://wiki.ubuntu.com/LaptopTestingTeam") that sometimes provides info on suspend/resume set up.

If you are using a nvidia or ati card with the proprietary driver you might need to search your laptop model 
here or through google (with ubuntu or linux) to see what others did to get suspend working.

---

### Post by buccaneere on 2008-11-10
Hi there phidia...

Hardy, pc hardware:

Microprocessor   	2.2 GHz AMD Turion ™ 64 X2 Dual-Core Mobile Technology TL-64
Microprocessor Cache 	512KB+512KB L2 Cache
Memory 	2048 MB DDR2 System Memory (2 Dimm)
Memory Max 	Max supported 2048 MB
Video Graphics 	NVIDIA GeForce Go 6150 (UMA)
Video Memory 	Up to 559 MB
Hard Drive 	240 GB (5400 RPM) Dual HDD - 120 GB x 2 (SATA)
Multimedia Drive 	LightScribe Super Multi 8X DVD±R/RW with Double Layer Support
Display 	17.0" WXGA+ High-Definition BrightView Widescreen (1440 x 900) 


If you got any ideas, chime in. I'm diggin' in the link you posted up. 

Thanks

---

### Post by buccaneere on 2008-11-10
Followed links to oblivion. Not too much specific leads on vids / resume / suspend...

---

### Post by baeksu on 2008-11-10
Looks like corrupt framebuffer. Probably the horizontal or vertical sync is wrong, and the screen goes like that.

Scared me the first time it happened to me, but it doesn't seem to cause damage.

Do you have any framebuffer settings you've put yourself in grub?

---

### Post by buccaneere on 2008-11-11
Hi baeksu...

No, I have not adjusted these settings that I know of; I presume they are at default settings.

How do I change them? Is the setting change only an increase or decrease? Or are there multiple increase/decrease settings, like audio equalization?

Thanks...

EDIT: This IS a multi-boot machine Vista/XPPro/Ubuntu, and I did modify grub for the multiboot installs. I think however that I only added boot sector location (or something like that), and I might have reversed the 2 HDD's in their bays.

---

### Post by buccaneere on 2008-11-11
Anyone?

---

