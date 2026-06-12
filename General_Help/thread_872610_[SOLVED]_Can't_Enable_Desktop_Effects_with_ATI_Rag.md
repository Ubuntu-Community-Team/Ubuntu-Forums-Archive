---
title: "[SOLVED] Can't Enable Desktop Effects with ATI Rage XL"
date: 2008-07-28
forum: General Help
---

### Post by theolster on 2008-07-28
Hi,

I can't get any 3D or desktop effects with my card.  I really need to get this to work because Ubuntu is effectively unusable and I want to be using ubuntu at work and not windows!  For example scrolling in Firefox is very slow.

During installation the installer detected my ATI Rage XL as using the generic ATI driver.  But this doesn't give 3d capabilities.

Does anyone know how to get this working???

The relavant part of xorg.conf looks like this:```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Rage XL"
	Busid		"PCI:4:2:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection
```

---

### Post by northern lights on 2008-07-28
Well, that's unfortunately due to the hardware.

The Rage XL chipset supports up to 8megs of SDRAM - what did you expect?

Sorry mate, without a new graphics card, no effects.

However you can grab some 64meg nVidia Geforce4 or similar for twenty bucks on eBay...

---

### Post by theolster on 2008-07-28
Really?  I'm surprised... the card seemed to work a lot better in windows.

---

### Post by northern lights on 2008-07-28
> **theolster said:**
> Really?  I'm surprised... the card seemed to work a lot better in windows.
Define "better".

You wanna enable "Desktop effects" right? What effects were there in your windows that the Rage could handle?

---

### Post by theolster on 2008-07-28
I understand what you are getting at, and am resigned to your solution.  But without compiz enabled, scrolling in firefox is still much slower than on windows.

I'll probably just give xubuntu a go and see how that performs.  It probably won't be much better though since I'm not short of ram (2G) or processor (3Ghz).

---

### Post by northern lights on 2008-07-28
> **theolster said:**
> I'll probably just give xubuntu a go and see how that performs.  It probably won't be much better though since I'm not short of ram (2G) or processor (3Ghz)

That system definitely deserves a better graphics card.

I've seen slow scrolling in firefox (w/ Hardy) on a classmates laptop (ATI Mobility Radeon - could be ATI related, doesn't have to be). I'm running an old 1.5 GHz AMD with a GeForce2MX 64megs, nothing fancy, but Hardy runs like a charm.

With Linux, a decent general advice is to stick to nVidia chipsets.

---

### Post by theolster on 2008-07-28
ATI might now be open source but I've always bought NVidia (this is a work PC) and I probably always will - I've got an old NV TNT and another slightly better NV at home, so I'll probably have to bring those in and give them a go!

---

### Post by Dougie187 on 2008-07-28
Also, I personally don't see how enabling compiz would make scrolling any faster in ubunut. If you graphics card is really that bad, i would think enabling compiz would make scrolling even slower.

---

### Post by theolster on 2008-07-28
I don't need/want compiz.  I just was trying to prove that the GPU diver was working so the scrolling in Firefox would be a little smoother!

I wasn't expecting only 8Mg of SDRAM!!! I'm used to only dealing with 'better' cards. So I assume that the driver is working fine, I'm just not going to get much out of the hardware.

---

