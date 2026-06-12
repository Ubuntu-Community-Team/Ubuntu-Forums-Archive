---
title: "Chromebook c720 Touchpad not responding (GalliumOS)"
date: 2016-03-11
forum: Hardware
---

### Post by munkymac on 2016-03-11
Got home from work the other day (where everything had been operating as normal) and my touchpad had completely stopped functioning. Running ```
xinput
``` gets me this output:

aaron@aaron-Peppy:~/Downloads $ xinput
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; HD WebCam                               	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]


As you can see, nothing is listed. I tried rebooting, and eventually even tried booting from USB, both the Gallium usb that I initially installed with, and also a Gnome USB I had. In none of those cases did the touchpad work. I'm pretty sure that means the touchpad is dead (or possibly the connection came loose), but I wanted to see if there was anything else I should try before cracking it open. Here's a link to the output of ```
sudo lshw
```: [http://pastebin.com/QLpa3ypa](http://pastebin.com/QLpa3ypa)


And here's the output of lspci:
aaron@aaron-Peppy:~ $ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:15.0 DMA controller: Intel Corporation 8 Series Low Power Sub-System DMA (rev 04)
00:15.1 Serial bus controller [0c80]: Intel Corporation 8 Series I2C Controller #0 (rev 04)
00:15.2 Serial bus controller [0c80]: Intel Corporation 8 Series I2C Controller #1 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev ff)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
00:1f.6 Signal processing controller: Intel Corporation 8 Series Thermal (rev 04)
01:00.0 Network controller: Qualcomm Atheros AR9462 Wireless Network Adapter (rev 01)

---

