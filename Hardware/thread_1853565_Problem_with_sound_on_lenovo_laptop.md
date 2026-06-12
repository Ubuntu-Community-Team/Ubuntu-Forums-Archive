---
title: "Problem with sound on lenovo laptop"
date: 2011-10-02
forum: Hardware
---

### Post by matrix72 on 2011-10-02
Hi all.

I have recently installed ubuntu 11.04 on my lenovo R61i laptop. The sound is working on start up, but after a short time, the sound does not work without restarting ubuntu. I don't know why this happens and how to solve it. Can someone please help me?

---

### Post by tgalati4 on 2011-10-02
Right after the sound fails, open a terminal and post the output of:

dmesg | tail -40

Also:

grep pulse /var/log/user.log

And did you try?

pulseaudio -k

That will usually restart the sound system if it crashes.  We need to find out why it is crashing.  You shouldn't have to reboot to restore sound.

---

### Post by matrix72 on 2011-10-04
Hi.

Thanks for your reply.
Again I have encountered the sound problem mentioned above.

This is the output of dmesg | tail -40:

[   14.717224] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one.
[   14.723746] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   14.761765] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   14.781598] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   14.848565] iwl3945 0000:03:00.0: Error setting Tx power (-5).
[   14.850375] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.890531] Bluetooth: L2CAP ver 2.15
[   14.890535] Bluetooth: L2CAP socket layer initialized
[   14.905089] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   14.905093] Bluetooth: BNEP filters: protocol multicast
[   14.916637] Bluetooth: SCO (Voice Link) ver 0.6
[   14.916641] Bluetooth: SCO socket layer initialized
[   15.002551] Bluetooth: RFCOMM TTY layer initialized
[   15.002559] Bluetooth: RFCOMM socket layer initialized
[   15.002561] Bluetooth: RFCOMM ver 1.11
[   15.015729] fbcon: inteldrmfb (fb0) is primary device
[   15.016883] Console: switching to colour frame buffer device 160x50
[   15.016923] fb0: inteldrmfb frame buffer device
[   15.016925] drm: registered panic notifier
[   15.022169] acpi device:02: registered as cooling_device2
[   15.023066] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   15.023853] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   15.025063] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   15.025125] HDA Intel 0000:00:1b.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   15.025130] hda_intel: probe_mask set to 0x1 for device 17aa:20ac
[   15.025222] HDA Intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   15.025261] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   15.388450] ppdev: user-space parallel port driver
[   15.571585] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   15.686345] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   19.158005] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   30.454106] wlan0: authenticate with 00:26:5a:fd:3e:a6 (try 1)
[   30.455958] wlan0: authenticated
[   30.456928] wlan0: associate with 00:26:5a:fd:3e:a6 (try 1)
[   30.459857] wlan0: RX AssocResp from 00:26:5a:fd:3e:a6 (capab=0x431 status=0 aid=1)
[   30.459861] wlan0: associated
[   30.461551] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.510463] Intel AES-NI instructions are not detected.
[   30.529377] padlock_aes: VIA PadLock not detected.
[   41.064020] wlan0: no IPv6 routers present


I have also tried the command "grep pulse /var/log/user.log", but there is no such file.

Using the "pulseaudio -k" does not help either.

---

### Post by matrix72 on 2011-10-06
Hi.

I have found the reason, i.e. when running a java applet with sun-java6, the sound somehow is turned off. When quitting the applet the sound turns on again. I have now installed openjava instead and the problem is now solved.

Anyway thx for ur reply.

---

