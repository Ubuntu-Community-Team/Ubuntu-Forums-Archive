---
title: "What is the speed of the Ram"
date: 2009-01-01
forum: Hardware
---

### Post by Merps on 2009-01-01
Old pc 128MB ram, P3 cpu

cat /proc/meminfo works and tells me the amount but doesn't tell me the speed

dmidecode --type memory   or --type 17 again tells me the amount but not the speed

how to find the speed of the ram, and by that I mean pc100 or pc133?

---

### Post by logos34 on 2009-01-01
hmm, good question...shouldn't be this hard.  Sometimes **sudo lshw** shows it (alas, not on mine though)

---

### Post by jespdj on 2009-01-01
You can probably also find this in the BIOS settings of your computer. Press Del (or whatever other key you need to press to get into the BIOS settings, it should be displayed on screen) right after you turn on the computer to get into the BIOS settings.

---

### Post by Merps on 2009-01-01
> **logos34 said:**
> hmm, good question...shouldn't be this hard.  Sometimes **sudo lshw** shows it (alas, not on mine though)

didn't find the lshw probably because it is running on a light linux distro due to age of pc.

---

### Post by Merps on 2009-01-01
> **jespdj said:**
> You can probably also find this in the BIOS settings of your computer. Press Del (or whatever other key you need to press to get into the BIOS settings, it should be displayed on screen) right after you turn on the computer to get into the BIOS settings.

I checked, sadly only says the size 128MB not the speed.

---

### Post by Merps on 2009-01-01
I tried "dmesg" with no luck either.

Then I went back and realised that "dmidecode --type memory" does give some potentially useful information:

128 MB
70 ns
Dimm SDRAM
Single Bank connection

Now can that be translated to a particular type of ram module say pc100 or 133 SDram?

However I have only found this information  "7.5 ns (PC133) instead of 10 ns (PC100)" on the net, so I am not sure how good the information from dmidecode really is.

---

### Post by logos34 on 2009-01-01
> **Merps said:**
> 
However I have only found this information  "7.5 ns (PC133) instead of 10 ns (PC100)" on the net, so I am not sure how good the information from dmidecode really is.

yeah, I saw the same thing...forgot how to translate ns into MHz/(PC?)...I can't believe there's not an easy linux command to get this info from the CLI. 

mine show this:

> Supported Speeds:
		70 ns
		60 ns
		50 ns

but says the current speed is

> Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2 3
	**Current Speed: 5 ns**
	Type: Unknown EDO
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

(I have NON-ECC DIMM 400MHz/(PC3200))

---

### Post by Merps on 2009-01-01
logos34, yes, it doesn't seem like dmidecode is the bible on this area.  There's got to be an easy and reliable way?

In the end I just pulled it and checked the sticker, pc100 no problems.

---

