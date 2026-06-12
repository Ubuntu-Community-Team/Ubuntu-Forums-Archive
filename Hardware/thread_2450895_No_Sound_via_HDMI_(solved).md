---
title: "No Sound via HDMI (solved)"
date: 2020-09-23
forum: Hardware
---

### Post by somamint on 2020-09-23
Hello,

i switched to Lubuntu on my old netbook (Thinkpad E145). So far everything works. But i can't figure out how to get audio working via HDMI.
I'm using the open source graphic driver

```
sudo lshw -c video
[sudo] password for somavakien: 
  *-display                 
       description: VGA compatible controller
       product: Kabini [Radeon HD 8240 / R3 Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:39 memory:e0000000-efffffff memory:f0000000-f07fffff ioport:4000(size=256) memory:f1500000-f153ffff memory:c0000-dffff

```

How can i install a different driver? 

Any Solution would be appreciate :)

---

### Post by guiverc on 2020-09-23
Which release of Lubuntu are you using?

Assuming you're using Lubuntu 20.04 LTS, I'd try using *Output Devices* on `pavucontrol` (Pulse Audio Volume Control) first, ie. from the manual

[https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html](https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html)

---

### Post by somamint on 2020-09-23
I'm using Lubuntu 19.10.

I tried it already with pavucontrol, but once i change the sound on output Devices to HDMI no sound will appear.

---

### Post by guiverc on 2020-09-23
Ubuntu 19.10 (along with all flavors like Lubuntu) is *End-of-Life*

I'd suggest you use a supported release of Lubuntu.

[http://fridge.ubuntu.com/2020/07/17/ubuntu-19-10-eoan-ermine-end-of-life-reached-on-july-17-2020/](http://fridge.ubuntu.com/2020/07/17/ubuntu-19-10-eoan-ermine-end-of-life-reached-on-july-17-2020/)
[https://lubuntu.me/lubuntu-19-10-end-of-life-and-current-support-statuses/](https://lubuntu.me/lubuntu-19-10-end-of-life-and-current-support-statuses/)

 [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by somamint on 2020-09-23
ok. so i Updatet to Lubuntu 20.04 LTS, but the sound problem is still the same

ok i got it :) thanks!

---

