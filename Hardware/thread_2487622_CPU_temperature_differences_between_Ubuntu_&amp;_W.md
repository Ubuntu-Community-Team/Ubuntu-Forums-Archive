---
title: "CPU temperature differences between Ubuntu &amp; Windows"
date: 2023-06-10
forum: Hardware
---

### Post by michael351 on 2023-06-10
I have a dual boot PC (Ubuntu & Windows 10) I use as a home theater device.
I noticed when I run Windows, the CPU temperature runs quite hot (~80 degrees C). When I am running Ubuntu, it is half that temperature (~40 degrees C).
Both measurements were observed when the CPU is relatively idle (just after logging in).

I did not expect this - anyone else observe this difference? I tend to run Ubuntu most of the time, but occasionally I'll load Windows to update the OS and use a few apps I don't have on Ubuntu.
(another reason why I like Ubuntu!)

---

### Post by TheFu on 2023-06-10
Probably GPU driver support for the video codec used isn't as good inside MS-Windows for your specific install.  I'd check inside Windows for a better GPU driver.  This situation pretty much never happens, since MS-Windows is the primary target OS for GPU vendors and their drivers.

With Ubuntu, if you have AMD or Intel GPUs, then the driver update automatically with the weekly patching you do.  On MS-Windows, I don't know when drivers get updated, if ever.  I've never seen or used Windows newer than Win7. I just couldn't agree with MSFT's new EULA terms.

There's another possibility.  The Linux sensor drivers that pull temperatures are broken and not providing the truth.  For AMD motherboards, poor sensor support is common.  Intel motherboards usually get sensor data on Linux years before AMD does.  I have a B450 with a Ryzen CPU.  While I get the CPU temp (1, not per core), I don't get any other temperatures from the motherboard. I do get the GPU and SSD/HDD temperatures, however.

---

