---
title: "Wi-Fi Won't Turn On"
date: 2016-08-28
forum: Hardware
---

### Post by luchian on 2016-08-28
I'm running Ubuntu GNOME (16.04.1 LTS)
I have a proprietary driver already loaded.

Hardware:
BCM4313 802.11bgn wireless network adapter

Driver:
Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)

Any and all help would be appreciated. I'm a newb, so you'll to tell me what terminal commands to run if you need additional information. Sorry for the inconvenience.

---

### Post by luchian on 2016-08-30
Solved.
Here was my process:
I turned off the Wi-Fi via my laptop's keyboard. The function key (f12) controls the Wi-Fi. So I turned OFF the Wi-Fi, which "disabled" the hardware.
I then turned it back ON. This enabled it and then I was able to connect my my Wi-Fi network.

Step 1: Turn Off/Disable Hardware (f12 for me)
Step 2: Turn On/Enable Hardware (f12 a second time for me)
Step 3: Connect to the Wi-Fi (and input password, obviously)

Then I was able to get and stay connected (so far). I'm submitting this follow-up via my Wi-Fi connection.

I had no idea that it was going to be something so simple. But maybe this will help someone else. I have no idea why I needed to turn off/disable and then turn on/enable, but it seems to have worked. Maybe this is the equivalent of rebooting your wireless adapter? I'm not sure. But it's working, and I'm not going to be too picky about that.

---

