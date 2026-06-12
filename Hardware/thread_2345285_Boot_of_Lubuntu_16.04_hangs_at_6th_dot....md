---
title: "Boot of Lubuntu 16.04 hangs at 6th dot..."
date: 2016-12-02
forum: Hardware
---

### Post by hvn2 on 2016-12-02
Hi,

I'm not sure if this really is a hardware issue, but on my new laptop (4 core, nVidia M2000M, ssd, no OS) I want Linux. After initial boot with GRUB, it doesn't matter which option (Live, direct install) I choose. I get a screen with lubuntu and the 5 dots under. The first 5 dots go quick, then on the new row of 5 dots it gets stuck on the 1st dot. I do observe the nouveau driver being loaded, but that's all.
I did check other posts about nVidia/Ubuntu 16.04, but I found no solution there.

Thanks,

hvn

---

### Post by hvn2 on 2016-12-02
OK, found the issue: in the BIOS/EFI it's the Optimum that's killiing. Going to basic graphics works,

---

