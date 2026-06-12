---
title: "Headphones disturbed"
date: 2010-05-03
forum: Hardware
---

### Post by palimmo on 2010-05-03
Hello.
My "Ubuntu laptop Karmic Koala 64-bit" is fine. Or almost.
There is a problem haunts me since the beginning:
headphones audio is disturbed. 
Either I'm listening music or the headphones are inserted without any audio signal is reproduced, I hear a noise in the background. That typical noise as if the volume is high.... But this is not ...

I can not find any place where regular headphones audio.

Can you help me, please?

Here there are more information about the device:

```
~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation G98M [GeForce G 105M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

```
~$ aplay -l
**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Sottoperiferiche: 0/1
  Sottoperiferica #0: subdevice #0
scheda 0: Intel [HDA Intel], dispositivo 1: Conexant Digital [Conexant Digital]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

```

```
~$ cat /proc/asound/card*/codec* | grep -i codec
Codec: Conexant CX20561 (Hermosa)

```

```
~$ dmesg | grep -i hda
[   16.701937] HDA Intel 0000:00:1b.0: power state changed by ACPI to D0
[   16.701957] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.702028] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.829598] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   16.829690] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.829743] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9

```

And:
[[img]http://img696.imageshack.us/img696/8804/schermataco.th.png[/img]](http://img696.imageshack.us/i/schermataco.png/)

---

### Post by mörgæs on 2010-05-03
Sound was one of the main problems in 9.10, but it has improved a lot in 10.04. Have you tried a 10.04 live boot?

---

### Post by palimmo on 2010-05-03
> **mörgæs said:**
> Sound was one of the main problems in 9.10, but it has improved a lot in 10.04. Have you tried a 10.04 live boot?

not yet.

---

### Post by palimmo on 2010-05-04
> **mörgæs said:**
> Sound was one of the main problems in 9.10, but it has improved a lot in 10.04. Have you tried a 10.04 live boot?


but... is there no other solution? Only change the version of Ubuntu?? :(

---

### Post by palimmo on 2010-05-05
:-?

---

### Post by lidex on 2010-05-05
Work through this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Make sure to install the alsa-backports.

---

