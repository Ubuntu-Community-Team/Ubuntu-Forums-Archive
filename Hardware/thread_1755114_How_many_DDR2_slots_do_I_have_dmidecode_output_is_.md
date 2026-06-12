---
title: "How many DDR2 slots do I have? dmidecode output is confusing."
date: 2011-05-10
forum: Hardware
---

### Post by brnetonboy on 2011-05-10
My motherboard has four DIMM slots for RAM (labeled XMM1, XMM2, XMM3, and XMM4). They look identical (one notch near the middle) except 1 & 3 are black plastic, 2 & 4 are white. I have only one DIMM in right now, in slot 1.

I'd assume they're all the same, but my [FONT="Fixedsys"]dmiencode[/FONT] output seems to indicate that 1 is DDR2, while the rest are just regular DDR?

[FONT="Fixedsys"]dmiencode --type 17[/FONT] output:

```
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0035, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0033
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
[B]	Locator: XMM1
[/B]	Bank Locator: Not Specified
[B]	Type: [COLOR="Red"]DDR2[/COLOR]
[/B]	Type Detail: Synchronous
	Speed: 400 MHz (2.5 ns)
	Manufacturer: JEDEC ID:C1 00 00 00 00 00 00 00
	Serial Number: 23211205
	Asset Tag: Not Specified
	Part Number: 64T128020HU5A

Handle 0x0036, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0033
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
[B]	Locator: XMM2
[/B]	Bank Locator: Not Specified
[B]	Type: [COLOR="Red"]DDR[/COLOR]
[/B]	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: JEDEC ID:
	Serial Number:  
	Asset Tag: Not Specified
	Part Number:  

Handle 0x0037, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0033
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
[B]	Locator: XMM3
[/B]	Bank Locator: Not Specified
[B]	Type: [COLOR="Red"]DDR[/COLOR]
[/B]	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: JEDEC ID:
	Serial Number:  
	Asset Tag: Not Specified
	Part Number:  

Handle 0x0038, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0033
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
[B]	Locator: XMM4
[/B]	Bank Locator: Not Specified
[B]	Type: [COLOR="Red"]DDR[/COLOR]
[/B]	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: JEDEC ID:
	Serial Number:  
	Asset Tag: Not Specified
	Part Number:  

```

I need to buy new RAM as the current ram is probably wrong (found it lying around). What type of RAM does my motherboard take? Once I figure out what type it is I'm just going to buy the max speed even though I'm sure it's a slower mobo.

(PS, I'm running 64 bit, I think.)

---

### Post by brnetonboy on 2011-05-10
Another thought: how much RAM can Ubuntu handle? I'm on Natty 64bit. Can I put 2GB DIMMs in all four slots?

---

### Post by brnetonboy on 2011-05-11
should this maybe have gone in a different forum?

---

### Post by RayVad on 2011-07-26
I think this is due to the fact that there are no other simms into to other slots. Dmidecode isn't able to determine the type of slot and it will not output info if nothing is in it. Dmidecode reads the info from you BIOS and only the ram module in the first slot in your case.

---

### Post by walt.smith1960 on 2011-07-26
If you know the model of your mother board, go to Crucial's site and use their memory advisor tool.  It will give the the type of memory and max supported.  You don't have to buy it there but Crucial does have a good rep AFAIK.  When I upgraded RAM on my desktop, I bought Crucial memory through Sears, of all places. They had the best $ and quick delivery.

---

