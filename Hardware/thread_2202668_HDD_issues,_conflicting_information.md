---
title: "HDD issues, conflicting information?"
date: 2014-01-30
forum: Hardware
---

### Post by Graham_Dancy on 2014-01-30
Hello, first time poster, long time lurker, recent victim of hugely frustrating problem.

Meat n Potatos:
Intel DG41MJ, 2.9 core2duo, 2gb ram, 300w PSU
Drive1 - toshiba 2.5" 80gb, 5 years old
Drive2 - seagate barracuda 3.5" 3tb, 1 year old
Drive3 - atapi cdrw/dvdrom
All drives sata
No PCI card or peripherals
OS - 12.10 server

Story
Machine run for about a year in this config. Drive errors began gradually on barracuda, mitigated for a time by shifting write loads onto 80gb (root) drive where possible leaving barracuda idle as much as possible, no issues occurred when reading data and was able to recover about 1.4tb without special measures.

No logs to post due to formats and repartitions but could recreate. DRDY ERR and CRCY (or something, cyclic redundancy was its definition) almost entirely, soft resetting link, udma 133,100,33 set in varying proportion. Short data writes seemed to be ok but anything prolonged would result in the drive giving up and going read only, after a few days of messing about it started taking the other drive with it leaving whole system posting IO error to all commands. Also noticed the tosh posting these errors but much harder to replicate without the other drive throwing spanners at it.

Smartctl results on both drives were PASS, this is where I get confused. Surely a dying drive would be reporting errors?

Swapped around power and sata cables to no effect, run ubuntu installer on both drives, flawless on the tosh, fails on the barracuda. Tried winserver 2k3 on barracuda for a giggle, failed.

still to try barracuda on known good board




My query is, has anyone here chased a similar problem? Is the SMART pass indicative of a SATA controller issue or could the barracuda still be broken in some way without posting to SMART? I've scratched a hole in my head trying to pin this one down.

Thanks in advance to anyone taking a crack at this.

---

### Post by andyfied on 2014-01-30
SMART data will catch a lot of up coming errors, but will not get them 100% of the time. If your Barracuda is going wonky, then try to back up everything on it and take it back to Seagate as it should be under warranty. Swapping the board will not help unless you also swap the ROM chip and you will need very good soldering skills. (And will void warranty.)

Good to see the Toshiba soldiering on, but at its age I'd consider replacing it as well.

---

### Post by Graham_Dancy on 2014-01-31
Thanks for the input.

Barracuda data is fully recovered so there's no panic here and at this point I've flattened both drives a few times to rule out partition table corruption (which was showing up in scans but appears to simply be a symptom opposed to a root cause). Key to solving this I suppose is to pop the drive into my desktop rig, only thing putting me off is disconnecting all its existing drives as a precaution, I'm lazy like that lol.

Would of course love to fill my server with shiny new gear but I'm somewhat fiscally challenged and often have to resort to using repurposed drives and scavenged parts, hence the old toshy laptop drive for hosting the OS. That and the box isn't for commercial use, its built as a home media box with some network infrastructure duties such as dns, dhcp and http filtering. Amusingly I woke up last night for a quick bio and it crossed my mind I could circumvent this sata controller issue with a PCI card, they go for buttons on ebay but it of course depends on the outcome of the transplant test.
In point of note, I've got 3 barracudas running, one is almost 8 years old and has been severely abused over its life! This is the first one I've known to be problematic!

Curious about your point of ROM, is that referring to a ROM chip on the drive or the mainboard?

---

