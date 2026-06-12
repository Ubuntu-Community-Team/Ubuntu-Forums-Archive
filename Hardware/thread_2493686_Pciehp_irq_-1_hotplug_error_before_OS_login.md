---
title: "Pciehp: irq -1 hotplug error before OS login"
date: 2023-12-21
forum: Hardware
---

### Post by archertech on 2023-12-21
Had this error appearing for a week or so, then my PC screen went black, lost all peripherals, but stayed powered on in the middle of a game. The PC would not boot up again, but powered on and gave the code 97 on the Gigabyte Z690 Master MB. I saw this code was related to graphics so I tested my vertical GPU mount, the PCIE slot on the motherboard, and the GPU. I reset the bios as well but it didn't work while the same hardware that was in there. Eventually I found that it booted back on with another GPU. This led me to think the 4090 died, but with the new GPU (AMD 5700) I can log into Windows fine, but when I get into Ubuntu it gives me the same error as it did before making me think its a kernel software issue. Is it possible that some linux updates or drivers can get things working again for my 4090? This is the exact error:

[ 0.939133] pcieport 000:00:1d.0: pciehp: Cannot get irq -1 for the hotplug controller
[ 0.939133] pcieport 000:00:1d.0: pciehp: Notification initialization failed (-1)

Then after about 1 second on the screen it boots into my Ubuntu login screen. This was the same error flash I ignored for a week or two before the whole thing went down with my last GPU.

Is there something that needs to be done to disable this hotplug issue entirely? I don't plug things in while the PC is on, so I don't need it at all.

---

### Post by Yellow Pasque on 2023-12-21
1. Make sure your BIOS is up to date.
2. Try booting with pciehp_poll_mode=1 if the message  persists.

---

