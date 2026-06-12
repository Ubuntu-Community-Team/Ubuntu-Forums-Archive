---
title: "Laptop won't turn on"
date: 2009-08-30
forum: Hardware
---

### Post by dbbolton on 2009-08-30
When I try to power on my laptop, the power light comes on, the fan turns on, and the hard disk light starts to blink regularly (about once per second). As of yesterday it would boot. However after a lot of strange freezes and kernel panics I suspected a hardware issue, particularly the hard drive. I got this error while running a live CD:
```

      hda: status timeout: status=0xd0 { Busy }
      ide: failed opcode was: unknown
      hda: no DRQ after issuing MULTWRITE_EXT
      ide0: reset: success

```Today I removed the RAM and hard disk and put them back in to insure good connections. After that, it wouldn't power on. I'm hoping the hard drive died and not the motherboard.

---

### Post by finito on 2009-08-30
In my experience,

This usually means that due to overheating one of your peripherals is gone.
Check your fan does it still work, if so try changing your HD.

I have seen mostly VGAs and Hard Drives lost to this issue.

---

### Post by dbbolton on 2009-08-30
I guess one of the sticks if RAM was still loose. After I removed them and put them back in again a second time, it booted. On all of my other computers, the PC speaker will beep when the RAM is loose.

---

