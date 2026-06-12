---
title: "ThinkPad T40, Suspend, AC and Battery"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by mperry on 2007-04-28
I have a Thinkpad T40 running an updated edgy to feisty here.  I believe on edgy this all worked somehow correctly but now there are some differences I've noted:

1) suspending for a long time, say 6 hours, causes the laptop to enter some deep sleep and it does not respond to anything besides a major power event; like unplugging, removing battery, restarting.

2) plugging the power cable in and out or making any power changes when the laptop suspends causes the laptop to not respond at all.  The little moon icon stays solidly lit and it does not respond.

I've tinkered around with a few different settings in /etc/default/acpi-settings like:

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

These cause a little better suspends but still the laptop has the problem with longer suspends.  I'm wondering if the laptop actually goes into hibernate mode after some period of time goes by but I have hibernate working as well and I should be able to power cycle the laptop and get everything back like it was.

Anybody seeing similar or even different things that you found an answer for, more questions about, or whatever?

---

### Post by raja on 2007-04-28
I have a thinkpad X40 and experienced similar problems with edgy. Never understood what the cause was. But it has been perfect with Feisty. I know it is not very helpful to you though.

---

### Post by Jingo on 2007-04-29
Same problem here. Just noticed 2 days ago.
Feisty suspended for ~½hour, and wouldn't wake up. Edgy suspend never worked for me. Dapper was fine.

Thinkpad T42, Radeon 7500

---

### Post by TeTeT on 2007-04-29
Does the T40p recover from suspend to RAM for you? When you run lspci -d 8086:24ca -vvn, do you see this:

```
00:1f.1 0101: 8086:24ca (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: 1014:052d
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at 01f0 [size=8]
        Region 1: I/O ports at 03f4 [size=1]
        Region 2: I/O ports at 0170 [size=8]
        Region 3: I/O ports at 0374 [size=1]
        Region 4: I/O ports at 1860 [size=16]
        Region 5: Memory at 50000000 (32-bit, non-prefetchable) [size=1K]

```

---

### Post by mperry on 2007-05-01
Hi-

I'll run the lspci command this evening.  Been away from this for a bit.  I reset the laptop to use apm to see if that made a difference since I was using acpi before.  Sad to say, that even apm does not bring the laptop back after a lid close event.  After only 30 minutes of apm suspend, the laptop fails to revive and forces me to take a more basic measure to wake it up.  This kinda makes Feisty useless on this laptop since its used by a variety of family members that don't know anything about Linux and just use firefox to browse the web.

Only thing I can think of doing is going back to edgy on it since suspends in acpi worked perfectly there.  I was going to check the acpi lid.sh script to check for something/anything; but since acpi is now out of the picture and I'm using apm, seems to me a more basic problem.

Any ideas with either acpi or apm?  The existing solution is sub-standard and I'll have to take the laptop to Vista since I have a second drive with Vista on it and suspend/hibernate works perfectly with it.

---

