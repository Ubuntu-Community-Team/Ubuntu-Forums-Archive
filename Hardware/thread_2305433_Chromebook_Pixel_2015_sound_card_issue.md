---
title: "Chromebook Pixel 2015 sound card issue"
date: 2015-12-05
forum: Hardware
---

### Post by 555loismustdie on 2015-12-05
I installed Ubuntu 15.10 on a Chromebook Pixel 2015, everything works flawlessly except for the fact that the integrated speakers do not work. If I use a USB headset they work fine. 
How can I go about forcing the drivers to install?
I've checked github pages with custom kernels, unfortunately installing them and rebooting results in nothing working (keyboard, touchoad, speakers, touchscreen, anything). 
Tried following the standard Ubuntu sound troubleshooting guide, no luck there.

I'm out of ideas, can anyone give me some commands to run for info needed to get stuff working? Not sure what entirely is needed but if I run  

lspci -v | grep -A7 -i "audio"

I get

00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
	Subsystem: Intel Corporation Broadwell-U Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e1218000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel

---

### Post by CharlesA on 2015-12-05
You need to use sudo whenever you use something like lshw or lspci.

```
sudo lspci -v | grep -A7 -i "audio"
```

---

### Post by 555loismustdie on 2015-12-05
> **CharlesA said:**
> You need to use sudo whenever you use something like lshw or lspci.

```
sudo lspci -v | grep -A7 -i "audio"
```

This is the result.

00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
	Subsystem: Intel Corporation Broadwell-U Audio Controller
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e1218000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Kernel driver in use: snd_hda_intel

What do I do from here?

---

### Post by CharlesA on 2015-12-05
Are you using pulseaudio or alsa? Most of the stuff I found mentioned that alsa worked, but pulse audio did not.
[http://askubuntu.com/questions/325418/no-sound-in-dual-os](http://askubuntu.com/questions/325418/no-sound-in-dual-os)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/857073](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/857073)

---

