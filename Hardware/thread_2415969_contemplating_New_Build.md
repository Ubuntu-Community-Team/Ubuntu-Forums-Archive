---
title: "contemplating New Build"
date: 2019-04-03
forum: Hardware
---

### Post by daniell59 on 2019-04-03
I would like to build around the Ryzen CPU with built in graphics. I wonder whether the Kernel 5.0 will give me trouble free performance. It would be good if I can simply use Ubuntu 18.04.

Thanks

---

### Post by TheFu on 2019-04-03
Are v5 kernels part of any installation today?   I vaguely recall that 4.19+ is needed for the onboard graphics to work.  New hardware always takes some time to become stable, as you know.  If you have an old GPU that can be used until the Ryzen 2-g CPUs are stable, then I would go that direction.

Depending on your budget and performance targets, it might be good to get a Ryzen 5 1600 for US$80 and use a cheapo GPU.  Only you can decide.  If I didn't build a Ryzen 2600 box in December, I'd be using the 1600 and would have saved over $100 on the build with how much RAM prices have dropped since then.

[https://ubuntuforums.org/showthread.php?t=2415753](https://ubuntuforums.org/showthread.php?t=2415753) is an issue with the v5 kernel.

---

### Post by daniell59 on 2019-04-03
Ubuntu 19.04 will be out shortly. Since it will comes with kernel 5.0, I thought that kernel will be available. I only want to install Ubuntu with long term support. I did not know that using a different video card will make a difference.

---

### Post by TheFu on 2019-04-03
> **daniell59 said:**
> Ubuntu 19.04 will be out shortly. Since it will comes with kernel 5.0, I thought that kernel will be available. I only want to install Ubuntu with long term support. I did not know that using a different video card will make a difference.

19.04 isn't LTS.  You'll need to wait for a dot release for 18.04 if LTS with v5 kernel support is needed.  If 18.04 won't boot into the installer, things get hard, just to get installed.

[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support) has the release support and kernels for each shown.  18.04.2 doesn't have a target kernel listed.

To use a different video card, disable the onboard GPU in the BIOS. That's how it works on Intel-based systems. Wouldn't expect Ryzen would be any different.  The BIOS on my B450 motherboard has a way to choose the primary GPU.

---

