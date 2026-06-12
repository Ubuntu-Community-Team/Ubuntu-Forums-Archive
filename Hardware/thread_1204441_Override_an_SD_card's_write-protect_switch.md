---
title: "Override an SD card's write-protect switch"
date: 2009-07-04
forum: Hardware
---

### Post by andrewkk on 2009-07-04
Is it possible to override the write-protection switch on an SD card in order to write to a "locked" card? As I understand it, [write-protection of an SD card]("http://en.wikipedia.org/wiki/Secure_Digital_card#Optional_write-protect_tab") is implemented in software so it is possible to instruct [some readers]("http://chdk.wikia.com/wiki/FAQ#Q._How_can_I_make_the_CHDK_program_load_automatically_at_startup.3F") to disregard that flag.

How can I try forcing Ubuntu to ignore an SD card's lock switch?

---

### Post by Boondoklife on 2009-07-04
> Because the notch is detected only by the reader, the protection can be overridden if desired (and supported by the reader).

This seems to point to hardware more than software.

---

### Post by zevans on 2010-04-14
Just experimenting with this myself. I've got a card that's working fine, except it's physically lost the sliding tab that locks and unlocks it. Open is unlocked, just like good old cassette tapes. :-)

I thought I'd try the "tape over the slot" trick but doesn't seem to work so like you I'm wondering if I can force an override as Wikipedia seems to imply...

---

### Post by zevans on 2010-04-14
Ha, fixed it. No software solution but I built the slot up with small pieces of electrical tape then taped a top layer on very firmly. 

The side of the card pushes a microswitch in the card reader so just taping over the slot wasn't enough - the tape moved into the slot rather than the switch closing inside the reader.

Working in the netbook now but don't think I'll rely on this one in the camera!

---

### Post by DeveloperNils on 2011-11-03
> **zevans said:**
> Ha, fixed it. No software solution but I built the slot up with small pieces of electrical tape then taped a top layer on very firmly. 

The side of the card pushes a microswitch in the card reader so just taping over the slot wasn't enough - the tape moved into the slot rather than the switch closing inside the reader.

Working in the netbook now but don't think I'll rely on this one in the camera!
This not a solution but your files are protected and can be easily saved. Put the SD chip with the write protect tab broken off in the SD slot. Copy the entire card onto an external hard drive or other storage device. Then get a new SD card and copy back to the new SD. I know this doesn't fix the card but there are some RISKS about trying to "build up" the write protect tab. If anything should come loose or tear it may get lodged in the SD Slot and prevent you from using the SD Slot. Fortunately the problem is not serious because the data is not lost and IS ACCESSIBLE READ-ONLY and can be downloaded.

Just a friendly caution.

---

