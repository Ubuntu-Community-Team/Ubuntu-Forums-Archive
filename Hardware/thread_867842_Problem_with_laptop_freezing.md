---
title: "Problem with laptop freezing"
date: 2008-07-23
forum: Hardware
---

### Post by kc9ddi on 2008-07-23
I'm having a bizarre problem with my Acer Aspire 7104WSMi laptop.  I'm using the latest version of kubuntu, fully up-to-date with apt-get, running kernel version 2.6.24-19-386.

Basically, every so often, each program the laptop is running will freeze, but not at the same time.  Usually what happens is I'll be working in one program, and then switch to another.  The program I switch to will freeze (ie, can't scroll, buttons won't work, etc).  I can switch back to the original program I was working in, and that will continue to work for a few seconds, and then freeze.  The whole computer never freezes, as I can always move the mouse, and when I move the move over KDE's buttons and window decorations, etc, I generally see the mouse over effect.  After a few seconds of this behavior, everything unfreezes all at once and starts working again.  This behavior seems to occur approximately every 5-8 minutes, and the freezes usually last about a total of 20 seconds each time (it varies a little from time-to-time, though).

I see the following interesting output in dmesg whenever this happens:

```

[465753.047856] ata1.01: qc timeout (cmd 0xa0)
[465753.047877] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[465753.047887] ata1.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[465753.047889]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[465753.047891]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[465753.047895] ata1.01: status: { DRDY ERR }
[465758.083152] ata1: port is slow to respond, please be patient (Status 0xd1)
[465763.074662] ata1: device not ready (errno=-16), forcing hardreset
[465763.074670] ata1: soft resetting link
[465763.492104] ata1.00: configured for UDMA/100
[465763.682517] ata1.01: configured for UDMA/25
[465763.682547] ata1: EH complete
[465763.698606] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[465763.707677] sd 0:0:0:0: [sda] Write Protect is off
[465763.707681] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[465763.738525] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[465763.747418] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[465763.754609] sd 0:0:0:0: [sda] Write Protect is off
[465763.754617] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[465763.779607] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Depending on the kernel version I'm using, this problem with happen with more or less frequency.  Also, it started with an upgrade to a certain kernel version, though I unfortunately don't remember which one.

Any thoughts on what the problem might be?

---

### Post by evets25 on 2008-07-23
Wow, that is a wonderfully vauge problem to diagnose. :D Perhaps it's related somehow to memory-usage? Just a theory, but what if the slow down is being caused by it writing stuff in and out of swap space? Normally this kind of slow down doesn't isn't caused by using swap space, but it could indicate a bigger problem. Some things to pursue: 

- How much ram do you have? (If it's 512 or less, this might be part of the problem) 
- What is your "swapiness" value set to? (if you have no idea what that means, probably the default of 60. 
- what is your memory usage like?
- Is there a lot of CPU being consumed while this lag occurs? (I would guess no)
- Is there a lot of disk reading/writing going on while the lag occurs? (I would guess yes) 
- How fast is your HD? (5400 RPM or 7200 RPM?)

glancing back at your post and the output from dmesg, I see lots of hard-drive related messages, but I don't know if that's normal gibberish, or problem-related gibberish.

Also, if your problem started with a kernel change, that would indicate a driver-level problem, something to do with the hard drive or sata controller, or something like that. 

/me shrugs.

---

