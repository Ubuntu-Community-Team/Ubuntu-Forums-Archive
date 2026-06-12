---
title: "Could a power shutdown screw the BIOS?"
date: 2013-03-08
forum: Hardware
---

### Post by nickdc on 2013-03-08
In a nutshell: healthy external SATA drive (functions fine in another desktop) connected to old Compaq 'presario' via a PCI SATA card (ALi M5281). Compaq internal drive (dual booting XP and Ubuntu) is also a SATA drive running from same card. I connect the external drive in order to make a partition clone. It is recognised in the BIOS and by Ubuntu and I create a folder ready for the clone image. I restart the pc, first loading the cloning software (Redo - Backup & Restore) on a live cd. Redo starts loading up as usual, then seems to hang. After a very long time of repeated dots I conclude something's amiss and attempt various key combinations to abort. The escape key produces a very fast screed of print-out, none of which makes much sense to me, and it doesn't stop. In desperation I do a power shutdown. From that point on, despite many attempts, the external SATA drive is not recognised in the BIOS. Whereas before at the "Identifying IDE drives" screen I got "xxoo" followed by the names of the two SATA drives, I now get the familiar "xxox" and just the internal drive listed.

I've checked the ext drive again on another pc and it's fine. I've checked the connections and cable and all seem good - after all, it worked a couple of hours ago. I've checked nothing's got changed in the BIOS. Everything else on the Compaq seems fine - Ubuntu booting up as normal. So, could the power shutdown have caused something to go wrong, or was that just a coincidence? Should I be removing and reinstalling the SATA card as a next step? I'm rather out of my depth here, and the problem is: it's not my pc, it's my partner's ... and she gets home tomorrow!! Any advice, suggestions, troubleshooting tips would be very welcome.

---

### Post by dcstar on 2013-03-08
Reset the BIOS to defaults and see if that makes a difference, also check the internal SATA/power cables have not been bumped out a bit.

---

### Post by nickdc on 2013-03-08
Thanks, David. I've tried both those suggestions, but no luck. Just can't figure it out, unless it's a problem on the SATA card that only affects the external port. I suppose the only way to test that is to have it out and try it in another machine ...groan!

---

### Post by nickdc on 2013-03-08
I've been prodding around a bit more and discovered one or two things. First, I was wrong in my original post, in that the main internal drive from which the OSs boot is *not* attached to the SATA card but to the standard IDE slot; it's a second internal drive, for storage etc, that's attached to the SATA card, but it works fine. If I remove its cable and attach the cable to the external drive instead, however, and reboot, nothing is recognised. Ie internal drive attached to internal slot on SATA card - no problem; external drive attached to either internal or external slot on SATA card - not detected. (And just to double-check: external drive attached to external SATA slot on a different pc - no problem!) What I'm not sure, is whether the internal and external slots on the SATA card are interchangeable, or could it be that the internal one will only detect a drive directly attached, not via an external enclosure? ... More investigation needed ... [Edit: It's looking that way (not interchangeable), as the bare drive is detected fine when connected directly to the internal port. So presumably there's either a BIOS issue or a hardware issue regarding the external port on the SATA card. Does that make sense?]
Also, looking more closely at the BIOS, it's the BIOS associated with the SATA card that is doing or failing to do the detection, ie ALi RAID BIOS V. 1.14 (M5283). I don't understand how it works, but I assume this somehow gets added to the mobo BIOS when the drivers for the SATA card are loaded? The SATA card was originally installed in Windows, long ago. How does Ubuntu deal with it? Is there a way I could get at that pre-OS boot BIOS configuration via the terminal? ... I'm struggling here ..

---

### Post by sudodus on 2013-03-08
I have used SATA and eSATA more or less interchangably. If I remember correctly, I have used a SATA-eSATA cable to connect a naked HDD via the esata port, and to connect an eSATA box directly to the mobo.

I think you have some kind of hardware error, for example a bad electrical connection, and it might be worthwhile to get new cables (SATA - SATA,  eSATA - eSATA and even SATA-eSATA). Something might also be wrong with the eSATA box.

---

### Post by nickdc on 2013-03-08
I'm certain you're right, sudodus. I'm making progress, in that I've been able to connect the naked "external" drive to the external port on the SATA card and power it from the internal (pc) psu, while the internal drive is still connected as always, and they were both detected. So the issue has to be largely with the external enclosure - though it works fine with another pc. I've got a spare enclosure, but unfortunately it has a "proper" e-SATA cable, which doesn't fit the standard SATA ports on the controller card, so I'm stymied. (I'm located in rural France, so no chance of popping round to my local store. I have to make do with the various bits I've collected over the last 20 years!) Thanks for the help.

---

### Post by nickdc on 2013-03-08
SOLVED after a fashion, since I'm still not sure what was causing the problem, but after taking the bare drive out and reinstalling it in the enclosure, it is at last working with both pcs. Much relief, and thanks again for the suggestions.

---

### Post by sudodus on 2013-03-08
Congratulations to solving your problems :KS

and you are welcome :-)

---

