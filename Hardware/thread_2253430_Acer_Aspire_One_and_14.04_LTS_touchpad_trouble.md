---
title: "Acer Aspire One and 14.04 LTS touchpad trouble"
date: 2014-11-19
forum: Hardware
---

### Post by gtomorrow on 2014-11-19
Hello, all. I'm having a problem with the touchpad intermittently coming and going. I have an Acer Aspire One D250 netbook. I've searched the forums and searched the internet and have found these "solutions", none of which have permanently solved the touchpad problem. The truly frustrating thing is that it's never reproducible.

1)```
sudo modprobe -r psmouse
sudo modprobe psmouse
xinput list
```
sometimes it works, sometimes it doesn't. Seems i have more success with this series of commands when a mouse is plugged in but that kinda defeats the purpose! My .bash_history is 95% just these commands! It was also suggested to do this (without the xinput command) from another TTY (ctrl-alt-F1) but again no permanent love.

2)```
gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true
```
no permanent solution here either.

3) xserver-xorg-input-synaptics is up to date (1.7.4) but i reinstalled anyway,just to make sure.

4) and according to [this thread]("http://ubuntuforums.org/showthread.php?t=2244958&page=2&p=13170583#post13170583"), updating the kernel to 3.17 will solve the touchpad problem...but it didn't!

Here is the output of dmesg | grep pnp...
```

[    0.504969] pnp: PnP ACPI init
[    0.576454] pnp 00:00: disabling [io  0x164e-0x164f] because it overlaps 0000:00:1c.2 BAR 13 [io  0x1000-0x2fff]
[    0.576910] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.577157] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.577416] pnp 00:03: Plug and Play ACPI device, IDs SYN1b1c SYN1b00 SYN0002 PNP0f13 (active)
[    0.577643] pnp: PnP ACPI: found 4 devices
[    2.062816] isapnp: Scanning for PnP cards...
[    2.373599] isapnp: No Plug & Play device found

```
The touchpad is working right now as I type. Very frustrating. I started with Ubuntu 10.10 (maybe earlier) on this machine and have upgraded up to 14.04 LTS. This problem happened very rarely before but as of 12.04 LTS has worsened to a daily reoccurance.

Any help would be greatly appreciated. I realize there are quite a few threads on this forum regarding touchpad problems but unfortunately none have helped me find a solution. I REALLY don't want to reinstall everything only for the fact that that may not resolve anything.

Thanks for reading this long post.

---

