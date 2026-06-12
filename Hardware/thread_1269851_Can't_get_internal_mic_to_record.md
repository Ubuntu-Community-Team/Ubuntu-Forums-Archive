---
title: "Can't get internal mic to record"
date: 2009-09-18
forum: Hardware
---

### Post by Sickafant on 2009-09-18
Hi I'm have a problem with my internal mic not working or not being detected. 

It used to work in 8.10. Over the past few months I have tried Ubuntu, Kubuntu and Xubuntu and it doesn't work in any of them. Currently I'm using Xubuntu 9.04. From what I can recall, some controls are now missing such as the input source choices. In 8.10 there was the choice of "Front mic" and "Mic" which were the internal mic and jack respectively. Now there's just "Mic" and "Line" (which doesn't seem to do anything). There also used to be a switch to use a digital input source which is no longer present.

My machine is an HP dv5-1008ca

this is my lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
08:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Please help I am a newb. Let me know if more info is needed.

---

### Post by Sickafant on 2009-10-18
I was able to get the Front Mic option to appear, as well as other missing controls working. I really went all over the place to find answers so hopefully I don't miss an obscure yet essential step.

To start off, I had to disable pulseaudio. There seems to be an issue with it and digital input where I can't hear anything I'm recording. It's possible that there's a workaround to allow pulse to support it, but everything is working so great without it that I won't bother to look.

So I disabled the daemon from automatically starting all the time
```
sudo vi /etc/pulse/client.conf
```
Find the line with 'autospawn' and set it to no. Uncomment the line if necessary.

Then I had to add a line to alsa-base.conf to get the correct controls detected.
```
sudo vi /etc/modprobe.d/alsa-base.conf
```
at the end of the file add the following line:
```
options snd-hda-intel model=hp-dv5
```

Restart and everything should be working. Be sure to choose your Digital Input Source as DigitalMic1 and Input Source to be 'Front Mic'. Raise and enable your capture and digital sliders to about 70-80%.

---

### Post by Dreadlock man on 2009-11-08
Hi Sickafant,

I have an HP pavilion dv4-1413, but it seems to got the same Audio devices that you listed above
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller

Im runnin(Hg Ubuntu 9.04. Ive tried what you posted, but nothing changed. I cant find the "DigitalMic1" choice nor the "front MIc". Where do they supossed to be? in the Audio Control Panel(HDA ATI ALSA MIXER)?
Thanks

---

### Post by Dreadlock man on 2009-11-11
Bump

---

