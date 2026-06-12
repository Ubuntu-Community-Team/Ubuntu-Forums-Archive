---
title: "HP 530 laptop often freezes at boot"
date: 2008-05-29
forum: Hardware
---

### Post by ngolian on 2008-05-29
My laptop often freezes up early in the boot sequence. It's an HP 530 Centrino Duo. I compile my own kernels, but I used the same options with Debian until a couple of weeks ago and didn't have so much trouble. It could be the intel_rng module causing the problem, because that's sometimes the last message before the freeze. I can't remember exactly what it says, but IIRC it's to do with it not working because there's no FWH.

But I think the real problem is the next step: setting the system clock. It seems to do it twice at each boot, AFAICT once during the initrd phase and again when booting from the real root. The crashes can happen at either instance.

Are there some kernel options or parameters I could try to get rid of this problem?

---

