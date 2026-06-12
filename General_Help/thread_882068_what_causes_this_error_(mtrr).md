---
title: "what causes this error? (mtrr)"
date: 2008-08-06
forum: General Help
---

### Post by MountainX on 2008-08-06
I'm getting this error:

```
mtrr: type mismatch for fd000000,800000 old: write-back new: write-combining
```

I'm having disk performance problems, so maybe this is related?

```

cat /proc/mtrr
reg00: base=0xe0000000 (3584MB), size= 512MB: uncachable, count=1
reg01: base=0x00000000 (   0MB), size=4096MB: write-back, count=1
reg02: base=0x100000000 (4096MB), size=2048MB: write-back, count=1
reg03: base=0x180000000 (6144MB), size= 512MB: write-back, count=1
```

What other things should I check?

Any suggestions on how to fix or troubleshoot this? Thanks.

---

### Post by MountainX on 2008-08-06
Hmmm... is this the memory address mtrr is complaining about?

```
03:01.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27) (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Unknown device 8008
	Flags: bus master, stepping, medium devsel, latency 32, IRQ 10
	Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
	I/O ports at d800 [size=256]
	Memory at fe7ff000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at fe7c0000 [disabled] [size=128K]
	Capabilities: <access denied>
```

Any recommendations to fix this?

It seems like mtrr is saying it changed the setting from write-back to write-combining, but /proc/mtrr still shows write-back (and it looks like that's what it is supposed to be)...

This is all new to me.

---

