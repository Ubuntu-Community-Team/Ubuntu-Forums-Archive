---
title: "Instant Shutdown, BANG! (Thinkpad, Feisty)"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by sammermpc on 2007-11-04
I've been happily using Feisty for awhile now.  Starting today (and it's happened twice), my x40 thinkpad has powered off by itself.  Not just shutdown -- it has just *CLICK* and off.  The battery was charged and it was plugged into the wall.  I have no idea what could be going on -- there is no report of errors before the crash, but I don't know exactly where to look.  In the system log, I found some register dumps -- this is AFTER restart, recovering from the crash.

Can anyone make sense of this and point me to what I should be worried about?  This is kind of terrifying, that the computer could switch off so ungracefully...I assume it's a hardware something, maybe I even just jiggled the battery off, though it was connected to the wall...

Here's from the log:```

Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Present:  0x01f70000 | Host ctl: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008003
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Timeout:  0x00000000 | Int stat: 0x000000c0
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: ===========================================
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Present:  0x01f20000 | Host ctl: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008003
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Timeout:  0x00000000 | Int stat: 0x000000c0
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.316000] sdhci: ===========================================
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Present:  0x01f20000 | Host ctl: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008003
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Timeout:  0x00000000 | Int stat: 0x000000c0
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: ===========================================
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Present:  0x01f70000 | Host ctl: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008003
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Timeout:  0x00000000 | Int stat: 0x000000c0
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.324000] sdhci: ===========================================
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Present:  0x01f40000 | Host ctl: 0x00000001
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008003
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: ===========================================
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Present:  0x01f70000 | Host ctl: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008003
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Timeout:  0x00000000 | Int stat: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000001
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.344000] sdhci: ===========================================
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Present:  0x01f70000 | Host ctl: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008007
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.348000] sdhci: ===========================================
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Present:  0x01f00000 | Host ctl: 0x00000001
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008007
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:04:50 localhost kernel: [  147.356000] sdhci: ===========================================
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Argument: 0x000001aa | Trn mode: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Present:  0x01f40000 | Host ctl: 0x00000001
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008003
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: ===========================================
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Argument: 0x000001aa | Trn mode: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Present:  0x01f40000 | Host ctl: 0x00000001
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008003
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:07:14 localhost kernel: [  291.296000] sdhci: ===========================================
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: ============== REGISTER DUMP ==============
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Argument: 0x000001aa | Trn mode: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Present:  0x01f40000 | Host ctl: 0x00000001
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Power:    0x0000000e | Blk gap:  0x00000000
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Wake-up:  0x00000000 | Clock:    0x00008007
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Timeout:  0x00000000 | Int stat: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Int enab: 0x00ff00fb | Sig enab: 0x00ff00fb
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
Nov  4 13:07:14 localhost kernel: [  291.300000] sdhci: ===========================================


```

---

