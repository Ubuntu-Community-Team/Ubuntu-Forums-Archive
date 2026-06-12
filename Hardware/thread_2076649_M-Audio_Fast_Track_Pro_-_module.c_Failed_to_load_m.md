---
title: "M-Audio Fast Track Pro - module.c Failed to load module &quot;module-alsa-card&quot;"
date: 2012-10-26
forum: Hardware
---

### Post by rotten777 on 2012-10-26
So some background information... The device actually does work, eventually. I turn it off, turn it back on, wait to see if it shows up, if yes-> it works, else ->turn it off, turn it back on, repeat;

The messages I get in the syslog are:

```
Oct 26 12:54:35 hws kernel: [240876.491512] usb 3-3.1.3: >new full-speed USB device number 19 using xhci_hcd
Oct 26 12:54:35 hws kernel: [240876.584808] usb 3-3.1.3: >New USB device found, idVendor=0763, idProduct=2012
Oct 26 12:54:35 hws kernel: [240876.584812] usb 3-3.1.3: >New USB device strings: Mfr=1, Product=2, SerialNumber=0
Oct 26 12:54:35 hws kernel: [240876.584815] usb 3-3.1.3: >Product: FastTrack Pro
Oct 26 12:54:35 hws kernel: [240876.584817] usb 3-3.1.3: >Manufacturer: M-Audio
Oct 26 12:54:35 hws mtp-probe: checking bus 3, device 19: "/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.1/3-3.1.3"
Oct 26 12:54:35 hws kernel: [240876.587302] usb-audio: Fast Track Pro switching to config #2
Oct 26 12:54:35 hws kernel: [240876.616642] usb-audio: Fast Track Pro config OK
Oct 26 12:54:35 hws mtp-probe: bus: 3, device: 19 was not an MTP device
Oct 26 12:54:35 hws udevd[11454]: error opening ATTR{/sys/devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3.1/3-3.1.3/3-3.1.3:1.0/sound/card1/controlC1/../uevent} for writing: No such file or directory
Oct 26 12:54:35 hws pulseaudio[2331]: [pulseaudio] module-alsa-card.c: Card '1' doesn't exist: No such file or directory
Oct 26 12:54:35 hws pulseaudio[2331]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="1" name="usb-M-Audio_FastTrack_Pro-00-Pro" card_name="alsa_card.usb-M-Audio_FastTrack_Pro-00-Pro" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.

```

I'm not entirely sure what is going on. Seriously if I change NOTHING, the device gets turned off, then turned back on, and if the kernel picks it up, it works like a charm.

Is there anywhere else I can start to look? Or is this just something I have to deal with. FYI, the motherboard's onboard audio never has a single issue but I have to move cables around just to get it working (I have this run into a Mackie mixer).

Thanks in advance!:guitar:

---

### Post by timetunnel on 2012-12-02
Hi. I've got the same problem. Did you figure out what's causing it?

---

### Post by rotten777 on 2012-12-03
> **timetunnel said:**
> Hi. I've got the same problem. Did you figure out what's causing it?

I did not. I gave up and moved to using the internal audio on the motherboard with optical spdif :(

---

