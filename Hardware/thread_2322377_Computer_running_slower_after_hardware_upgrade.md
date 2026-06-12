---
title: "Computer running slower after hardware upgrade"
date: 2016-04-27
forum: Hardware
---

### Post by projectbronco on 2016-04-27
So, I have an older desktop that I decided to "upgrade".
By upgrade, I mean max out the motherboard and see if I could get a few more years out of it.

**Here is what I started out with.**

*MOBO:*
MSI K9A2 Platinum

*Processor:*
AMD Phenom X4 9950 2.6 GHz Quad-Core

*Memory:*
G.Skill 4GB 240-Pin DDR2-1066

*Video:*
ATI Radeon X800 Pro 256MB

*Power Supply:*
GreenME 650W

**Here is what I ended up with/currently have.**

*Same MOBO.*

*Processor:*
AMD Phenom II X4 965 3.4 GHz quad core socket AM3 CPU Deneb

*Memory:*
G.Skill 8GB 240-Pin DDR2-1066

*Video:*
PNY NVIDIA GeForce GTS 250 1GB Video Card PCI-E 2xDVI VCGGTS2501XPB Blue Board

*Same Power Supply.*

I am currently running Ubuntu 15.10 and am using the proprietary drivers.
The system seems to think the processor is an 800mhz processor!
What the crap!
Tasks that I was able to do previously, are now lagging and running very slow.
All of these components are supported by the motherboard as per the website.

Any help would be appreciated. I'm not expecting blazing fast, but my youtube videos shouldn't be buffering on HD when before, they were streaming.
Also, video rendering is slower, when it should be much better with this card. Again, not super fast, but 256MB to 1GB should be substantial I would hope...

Thank you for any help!

Also, please, have a wonderful day. :)

---

### Post by projectbronco on 2016-04-27
Well, someone had replied to the post asking me to upgrade my drivers, I did but I still have the same drivers.
Thank you for your reply, whomever you are. ;)

Here is a picture of my Additional Drivers screen:
[ATTACH=CONFIG]268676[/ATTACH]

---

### Post by weatherman2 on 2016-04-27
Does your motherboard  truly support that CPU?  Did you upgrade your BIOS to the most recent available from the manufacturer?

I was recently playing with an old laptop.  I tried to upgrade the CPU.  It booted up just fine, but as with yours the clock frequency was showing much slower than the original (slower) CPU.  Turns out the chipset on my laptop motherboard does not support the faster FSB of the faster CPU, so apparently it downshifts the CPU to the minimum speed.  Not even a BIOS upgrade would have fixed that - it was a limitation of the motherboard chipset.  In retrospect, I'm surprised it booted at all!

---

### Post by projectbronco on 2016-04-27
> **weatherman2 said:**
> Does your motherboard  truly support that CPU?  Did you upgrade your BIOS to the most recent available from the manufacturer?

I was recently playing with an old laptop.  I tried to upgrade the CPU.  It booted up just fine, but as with yours the clock frequency was showing much slower than the original (slower) CPU.  Turns out the chipset on my laptop motherboard does not support the faster FSB of the faster CPU, so apparently it downshifts the CPU to the minimum speed.  Not even a BIOS upgrade would have fixed that - it was a limitation of the motherboard chipset.  In retrospect, I'm surprised it booted at all!

No, I never did upgrade the BIOS...I'll look into that this evening.
Thanks, I appreciate your feedback and I'll let you know what I find out.

---

### Post by Yellow Pasque on 2016-04-28
The mobo's CPU compatibility list says you need BIOS version 1.9 or later.

You can check your current BIOS version with dmidecode
```
sudo dmidecode -t bios
```

---

### Post by projectbronco on 2016-04-28
> **Temüjin said:**
> The mobo's CPU compatibility list says you need BIOS version 1.9 or later.

You can check your current BIOS version with dmidecode
```
sudo dmidecode -t bios
```

I agree that the BIOS is the problem. Though, I tried to upgrade it last night with a USB stick that said it was bootable and it failed to do anything...
I've also attempted booting with a CD.
I extracted the zipped contents then dragged them to the USB.
I did the same with the CD when that didn't work.
I then hit F11 to select and force boot said device.

Am I missing something?

Here is the output of the dmidecode, I only have BIOS Version 1.4.
I am attempting to upgrade to 1.B, which is the newest available from MSI for my board.

```
Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: V1.4
	Release Date: 03/12/2008
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.14

Handle 0x002A, DMI type 13, 22 bytes
BIOS Language Information
	Language Description Format: Abbreviated
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

```

Thanks again!

---

### Post by weatherman2 on 2016-04-29
If your motherboard supports USB upgrade of BIOS, that's the way I would do it. I don't really remember how I did it the last time I upgraded an MSI board.  Probably the USB drive must be FAT32-formatted?  MSI should have exact instructions on their website and it should be fairly easy.

---

### Post by Yellow Pasque on 2016-04-29
You don't want to boot the USB. If you have a BIOS that supports flashing from a USB stick, it's often a specific F-key you hit during POST. You may have to disable the boot splash screen in your BIOS to see it, or look at the mobo manual.

---

### Post by Yellow Pasque on 2016-04-29
Hmm, it looks like the BIOS update is in .exe format, so you may have to look at making a FreeDOS boot stick and running it in that environment.

---

### Post by projectbronco on 2016-05-02
> **weatherman2 said:**
> If your motherboard supports USB upgrade of BIOS, that's the way I would do it. I don't really remember how I did it the last time I upgraded an MSI board.  Probably the USB drive must be FAT32-formatted?  MSI should have exact instructions on their website and it should be fairly easy.

Found that and have tried a few times without success. Perhaps I am missing some setting?...

> **Temüjin said:**
> Hmm, it looks like the BIOS update is in .exe format, so you may have to look at making a FreeDOS boot stick and running it in that environment.

Thanks, I'll try that this week. I haven't been able devote time to it because I've been using the computer and have been running for work. Though, it's a catch 22 because the computer is bogging down while I'm trying to do work on it.
I'll try and figure out the freedos boot stick.

---

### Post by projectbronco on 2016-05-12
OK, I couldn't figure out how to do the freedos way...Yeah...I know. I can build them, but flashing the BIOS stumped me. I took it into a local repair shop and had them do it. It was taking me too long to try and figure it out.
Thank you all for your input and help. I appreciate your time, especially.

---

