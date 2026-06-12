---
title: "configure bose companion 5"
date: 2012-04-28
forum: Hardware
---

### Post by mario.almeida on 2012-04-28
Hi All,

I installed Ubuntu 12.04 32bit and need help to configure Bose Companion 5 speakers.

Below are some errors, can someone help me?


```
Apr 28 23:00:51 margarida AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/5542a42f14734dd1b79410ed78f7b810
Apr 28 23:00:51 margarida AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/bbeab195273d4cfcac41e04c77ac7ab3
Apr 28 23:00:51 margarida &#65279;AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'ubuntuone-control-panel-qt')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
Apr 28 23:00:51 margarida kernel: [ 1533.533686] usb 7-1: new full-speed USB device number 6 using uhci_hcd
Apr 28 23:00:51 margarida mtp-probe: checking bus 7, device 6: "/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1"
Apr 28 23:00:52 margarida kernel: [ 1533.731508] 6:1:1: cannot get freq at ep 0x1
Apr 28 23:00:52 margarida mtp-probe: bus: 7, device: 6 was not an MTP device
Apr 28 23:00:52 margarida kernel: [ 1533.740700] generic-usb 0003:05A7:1020.0008: hiddev0,hidraw2: USB HID v1.10 Device [Bose Corporation Bose USB Audio] on usb-0000:00:1d.1-1/input2
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-Bose_Corporation_Bose_USB_Audio-00-Audio" card_name="alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-Bose_Corporation_Bose_USB_Audio-00-Audio" card_name="alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-Bose_Corporation_Bose_USB_Audio-00-Audio" card_name="alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-Bose_Corporation_Bose_USB_Audio-00-Audio" card_name="alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-Bose_Corporation_Bose_USB_Audio-00-Audio" card_name="alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module-alsa-card.c: Failed to find a working profile.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module.c: Failed to load module "module-alsa-card" (argument: "device_id="2" name="usb-Bose_Corporation_Bose_USB_Audio-00-Audio" card_name="alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1""): initialization failed.
Apr 28 23:00:52 margarida pulseaudio[2135]: [pulseaudio] module-udev-detect.c: Tried to configure /devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/sound/card2 (alsa_card.usb-Bose_Corporation_Bose_USB_Audio-00-Audio) more often than 5 times in 10s

```

---

