---
title: "[SOLVED] hmmmmmmm"
date: 2008-11-15
forum: Hardware
---

### Post by theozzlives on 2008-11-15
I'm confused, my ad for my Dell Inspiron says it's a 2.0 GHz, but all diagnostic software says it's a 1.73 GHz. My book says I have a Intel Core Duo, but the sticker says I have a Dual Core??? Does Dell not know what their talking about? This is why I hate Brand Names, wish I could build a "clone"' laptop!

---

### Post by blackened on 2008-11-15
All Core 2 Duos are dual core. The Core Solos are the single cores of that line.

It could be misreporting the cpu speed, but I doubt it. It's likely a t5300. What model number is your machine? Did you customize it during ordering?

---

### Post by theozzlives on 2008-11-15
IT'S A Inspiron 1525, and my mom bought it for my B-Day at Best Buy, that discussion and a core duo is supposed to be a step up from the older dual core

---

### Post by blackened on 2008-11-15
All "dual core" means is that the processor has two cores. It's not a brand name like "Celeron", "Pentium", or "Core 2 Duo" (all of which have or are dual core models), so it having a sticker that says "Dual Core" is not a misnomer nor does it make the processor inferior to any other, but simply denotes that the processor in your particular machine has two cores.

It seems that the 1525s are all supposed to be 2GHZ processors (ranging from Celeron, Pentium, and C2D), but yours is either being throttled by the OS or it's not being recognized properly.

---

### Post by theozzlives on 2008-11-15
> **blackened said:**
> All "dual core" means is that the processor has two cores. It's not a brand name like "Celeron", "Pentium", or "Core 2 Duo" (all of which have or are dual core models), so it having a sticker that says "Dual Core" is not a misnomer nor does it make the processor inferior to any other, but simply denotes that the processor in your particular machine has two cores.

It seems that the 1525s are all supposed to be 2GHZ processors (ranging from Celeron, Pentium, and C2D), but yours is either being throttled by the OS or it's not being recognized properly.

I'm running Ubuntu 64???

---

### Post by blackened on 2008-11-15
> **theozzlives said:**
> I'm running Ubuntu 64???

I don't know, are you? If so, then try running the 32 bit live cd and see how it recognizes your cpu. Or try firing up everest in windows to check it out. I don't know if any of those machines shipped with the t5300 or similar.

---

### Post by cdtech on 2008-11-15
To find the proc information along with the board info, you can use the command:
```
sudo dmidecode
```

---

### Post by theozzlives on 2008-11-15
> **cdtech said:**
> To find the proc information along with the board info, you can use the command:
```
sudo dmidecode
```

1733 MHz

---

### Post by blackened on 2008-11-15
Does it list your processor model?

---

### Post by theozzlives on 2008-11-16
> **blackened said:**
> Does it list your processor model?

Handle 0x0400, DMI type 4, 40 bytes
Processor Information
	Socket Designation: Microprocessor
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: Intel
	ID: FD 06 00 00 FF FB EB BF
	Version: Not Specified
	Voltage: 3.3 V
	External Clock: 133 MHz
	Max Speed: 1733 MHz
	Current Speed: 1733 MHz
	Status: Populated, Enabled
	Upgrade: None
	L1 Cache Handle: 0x0700
	L2 Cache Handle: 0x0701
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable

that's what it says, I sound stupid but I can run circles around the best in DOS.... I just hate Windows

---

