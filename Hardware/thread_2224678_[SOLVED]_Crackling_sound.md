---
title: "[SOLVED] Crackling sound"
date: 2014-05-17
forum: Hardware
---

### Post by balthier82 on 2014-05-17
Hello everyone, 

I recently installed Ubuntu 14.04. I have a problem with the audio when I connect an external monitor to the HDMI output. The audio is very scratchy. 
If I play the sound for a while, the sound stops being disturbed. If I pause the audio, I wait a bit and then I restart the audio, the audio noise again.

The hardware information are the following:

1) By typing **lspci** come out this information:

```
[COLOR=#555555][FONT=Monaco]00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M][/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Redwood HDMI Audio [Radeon HD 5000 Series][/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]02:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 03)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]7f:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)[/FONT][/COLOR]
```

2) With the command **cat /proc/asound/cards**:

```
[COLOR=#555555][FONT=Monaco]0 [MID            ]: HDA-Intel - HDA Intel MID[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]                      HDA Intel MID at 0xd4100000 irq 48[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco] 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]                      HDA ATI HDMI at 0xd4020000 irq 49[/FONT][/COLOR]
```

3) With **aplay -l **(is in italian):

```
[COLOR=#555555][FONT=Monaco]scheda 0: MID [HDA Intel MID], dispositivo 0: 92HD81B1X5 Analog [92HD81B1X5 Analog][/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Sottoperiferiche: 1/1[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Sottoperiferica #0: subdevice #0[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]scheda 1: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0][/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Sottoperiferiche: 1/1[/FONT][/COLOR]
[COLOR=#555555][FONT=Monaco]  Sottoperiferica #0: subdevice #0[/FONT][/COLOR]
```

I have a HP Pavilion dv6 3149sl.
I have already installed the drivers for the ATI video card (if this information can be useful).

I hope you can help me. :(

Thanks!!

---

### Post by T.J. on 2014-05-17
If you are using Pulseaudio - which is likely, it  has had a long history of being poorly handling certain audio chipset drivers. You may be able to solve your problem by adjusting the the driver parameters in the file: /etc/pulse/default.pa. You will need to have administrator permission to do this. Be sure to make a backup copy of the file before you make changes, just in case.


Edit the line:
load-module module-udev-detect

and add "tsched=0" so it will be:

load-module module-udev-detect tsched=0

Save it, and then preferably reboot, just to be on the safe side. Don't worry, this parameter should be perfectly safe to use. It will force PulseAudio try to not bulldoze over the sound driver's timing by forcing the scheduler to 0.

Hopefully, that will do it. Let me know if it persists.

---

### Post by balthier82 on 2014-05-18
You are a genius! Thanks the problem is solved! :D

---

