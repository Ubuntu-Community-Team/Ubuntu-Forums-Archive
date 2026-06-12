---
title: "Constant graphical glitches and crashing. Please help."
date: 2008-08-13
forum: General Help
---

### Post by spintriae on 2008-08-13
I've included a screenshot of what I'm dealing with. It's been doing this for three days now and I've done nothing to provoke it: changed nothing; installed nothing. It works for a little while at startup and begins glitching after a few minutes. The glitches get worse until eventually the system freezes, CTRL+ALT+BACKSPACE doesn't work and I have to hard reset. My system has crashed at least 40 times I assume because I've had two forced disk checks! One of those crashes corrupted my disk:

```
[   95.455655] eth1: no IPv6 routers present
[  102.118019] EXT3-fs error (device hdd1): ext3_check_descriptors: Block bitmap for group 442 not in group (block 148701184)!
[  102.135809] EXT3-fs: group descriptors corrupted!
[  209.035595] EXT3-fs error (device hdd1): ext3_check_descriptors: Block bitmap for group 442 not in group (block 148701184)!
[  209.037360] EXT3-fs: group descriptors corrupted!
[  218.566903] EXT3-fs error (device hdd1): ext3_check_descriptors: Block bitmap for group 442 not in group (block 148701184)!
[  218.574347] EXT3-fs: group descriptors corrupted!
[  595.328828] kjournald starting.  Commit interval 5 seconds
[  595.344544] EXT3 FS on hdd1, internal journal
[  595.344695] EXT3-fs: mounted filesystem with ordered data mode.
```

As you can see, this is a serious problem. Please help me troubleshoot it. My video card it a Voodoo3. Any other info I should post, let me know. Thanks.

---

### Post by ofb on 2008-08-15
Ouch. Sounds like bad hardware trouble.

Couple of starting points...

First fire up a LiveCD; isolate the drive. If the LiveCD seems to run fine, then I'd be suspecting drive failure rather than motherboard.

Are you familiar with working with the inside of your computer? If so, I'd suggest getting in there with a flashlight and looking for bulged or burst capacitors. Another hardware issue I've had that spawned random crashes was a failed fan on a vid card. Check that it spins freely.

Back to the drive, check this thread for running Smartmontools. You can do that from the LiveCD.
[http://ubuntuforums.org/showthread.php?t=690047](http://ubuntuforums.org/showthread.php?t=690047)

Tracing this sort of thing is probably going to be very tedious, so crank up your patience and sense of humour.

Also, is it summer where you are? Summer heat is notorious for pushing marginal systems over the edge. Make sure all your fans are spinning, and the box can breath.

---

