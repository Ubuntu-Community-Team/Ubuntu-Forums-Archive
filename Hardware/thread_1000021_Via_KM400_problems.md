---
title: "Via KM400 problems"
date: 2008-12-02
forum: Hardware
---

### Post by mikeygstl on 2008-12-02
using an ECS P4M800-M board with onboard video.  BIOS is set for 32MB of shared memory, and the AGP is also set to 32MB.  OpenChrome seems to not see the amount of video memory available:

(--) CHROME(0): Chipset: KM400/KN400
(--) CHROME(0): Chipset revision: 0
(--) CHROME(0): Probed amount of VideoRAM = 1024 kB

but then further down I see this:

(==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
(==) CHROME(0): Will try to allocate 32768 kB of AGP memory.

followed by:

(II) CHROME(0): Not using default mode "1024x768" (insufficient memory for mode)

I have verified that both the drm and via kernel modules are loaded.

Anyone have any ideas?  Trying to convince my friend to swap from windows to ubuntu, but if I can't get a decent resolution on this thing, that will be a bit hard...

Attached are a full X log and config.

Thanks in advance!

-Mike

---

### Post by Ilya.A on 2009-08-13
You should use option 'VideoRAM' in your xorg.conf like this:

Option "VideoRAM" "32768"

man page say's that this option should never be needed :)

---

