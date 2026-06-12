---
title: "Dell Vostro A180 with NVIDIA 8400 GS - Weird Sound Problem"
date: 2009-04-29
forum: Hardware
---

### Post by chief_officer on 2009-04-29
<-- THIS IS A CROSS-POST. THE ORIGINAL POST IS IN LQ. BELOW IS COPIED & PASTED FROM THE ORIGINAL. -->

Friends,

I have just purchased a Dell Vostro A180 desktop with the following specs:

CPU: Intel Dual Core E2200 [Running at 2.20 GHZ]
RAM: 1 GB
HDD: 160 GB Western Digital Caviar at 7200 RPM
Mainboard: Foxconn
Graphics Adapter: On board Intel GMA 950
Chipset: Intel GM 945 + ICH7
PSU: 185 Watt
Optical Drive: Optiarc Super Multi

and had a small surgery on it. Added:

Graphics Adapter: NVIDIA 8400 GS Asus Silent PCIx
Card Reader: Internal, 20-in-1, 3.5"
RAM: 1 GB [making a total 2 GB]
USB Hub: 7-port.
Additional Equipment: Maxtor 750 GB External Drive, Thermaltake home-made external disk 500 GB, USB keyboard, PS2 mouse

NVIDIA card is connected to my PHILIPS 220XW screen with HDMI. The card does not have an HDMI out, so I used DVI-HDMI connector. So, the connection is Graphics card - DVI/HDMI connector - HDMI Cable - Monitor. Monitor's power is not connected to the computer, independently connected to the UPS.

The desktop came with Ubuntu 8.04 and I installed 8.10 and then 9.04.

In all cases, after the installation of the NVIDIA's proprietary driver, the output went extremely bad [like shadows/beveled edges around the fonts and icons] and a strange sound came from the monitor's speakers [like the sound you hear from the VHF handsets.]

Thinking that the strange, disturbing sounds may be due to some incompatibility of the drivers, I have tried openSUSE 11.1 and installed the NVIDIA drivers manually and ran sax2 -r -m 0=nvidia but had the problem again.

I wonder what could be the reason for that. It does not seem a driver problem, since without the NVIDIA's drivers, the output is as it should be. But when I install the drivers and reboot, the strange sounds come from the monitor. 

I suspect that the reason might be due to the PSU, which can not deliver the power that the peripherals require and thus the graphics card can not drain enough watts to utilize its 3D capabilities.

hwinfo and lspci commands properly recognize the card as NVIDIA 8400 GS without any problems.

Any ideas?

Thank you all in advance,

---

