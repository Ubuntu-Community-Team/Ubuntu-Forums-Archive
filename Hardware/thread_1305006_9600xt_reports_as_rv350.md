---
title: "9600xt reports as rv350"
date: 2009-10-29
forum: Hardware
---

### Post by tcchris on 2009-10-29
I just installed a 9600xt in my computer running Karmic .P4 2.8 HT 1.5G DDR
The 9600xt should be rv360 , but the output of lspci -v 
is 

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
	Subsystem: ATI Technologies Inc Device 0002
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at de00 [size=256]
	Memory at fe9e0000 (32-bit, non-prefetchable) [size=64K]
	Expansion ROM at fea00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeon, radeonfb

01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)
	Subsystem: ATI Technologies Inc Device 0003
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at e0000000 (32-bit, prefetchable) [size=128M]
	Memory at fe9f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>


This detects the card as a rv350 .
Also rovclock -i reports the clock speeds as 

Core: 249.75 MHz, Mem: 297.0 MHz

I thought these should be 500 and 600 MHz


My card works , I just want to be sure I am getting what I should out of it .
Any help would be appreciated , like I said it works , so if this is normal , I am fine with it .
I just want to be sure I am getting the most out of my tired old computer

---

### Post by tcchris on 2009-10-30
Anyone know if this is normal ?

---

### Post by kiwibonga on 2009-11-08
"bump" as they say...

I've got the same card, and I also get the same results. The 9600xt is listed as RV350 AR, unlike the "regular" 9600 (or 9600 PRO) which is just RV350... Technically, it should be RV360, as they call it on the box, but the chip is essentially the same hardware with slightly better performance...

About the frequencies, they're accurate... It's 250/300, but 500/600 DDR.

Unfortunately, I can't really help... I'm in the same boat... I've tried countless things. What I know for sure is that ATI dropped support for the card in recent fglrx versions, so now all we can do is use the open source radeon driver... And performance is absolute crap :-( (but it's still a big step up compared to the software renderer!)

---

