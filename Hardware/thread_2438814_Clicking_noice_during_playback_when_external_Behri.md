---
title: "Clicking noice during playback when external Behringer card is connected via USB"
date: 2020-03-18
forum: Hardware
---

### Post by jacek.gajek on 2020-03-18
I encounter a clicking noice every second. It makes using headphones impossible because it could destroy hearing in a long run - the clicking level isn't affected by volume control.
I don't think it's relevant to playback software due to details described below. I use Chrome/youtube and foobar2000, though.

I dual-boot with Windows 10. Obviously, there is no problem with sound in Windows.
I use an external sound card, connected with USB (**Behringer UM2**).
The problem does **NOT** appear if I switch to the internal sound card

The symptoms were desribed in some datey reports, but solutions provided didn't work for me:

[https://daedtech.com/fixing-the-crackle-and-pop-in-ubuntu-sound/](https://daedtech.com/fixing-the-crackle-and-pop-in-ubuntu-sound/)

[https://ubuntuforums.org/showthread.php?t=1335395](https://ubuntuforums.org/showthread.php?t=1335395)

system info (from settings/About)
31,2 GiB
Intel® Core™ i7-9750H CPU @ 2.60GHz × 12 
GeForce GTX 1660 Ti/PCIe/SSE2
3.34.2
64-bit
2,5 TB

 lspci -v returns
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
	DeviceName: Onboard - Sound
	Subsystem: Micro-Star International Co., Ltd. [MSI] Cannon Lake PCH cAVS
	Flags: bus master, fast devsel, latency 32, IRQ 160
	Memory at a5410000 (64-bit, non-prefetchable) [size=16K]
	Memory at a5100000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [80] Vendor Specific Information: Len=14 <?>
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel, snd_soc_skl, sof_pci_dev



whether Behringer is connected or not.
in Settings/Audio Output there is an option
PCM2902 Audio Codec

---

