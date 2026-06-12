---
title: "Audio Output not working over DisplayPort/HDMI with Intel HD Audio/RealTek ALC662"
date: 2014-05-19
forum: Hardware
---

### Post by Pascal_Jerney on 2014-05-19
Hi there!

I installed Lubuntu 14.04 on my HP Elite 8000 Ultra  Slim Desktop. The Audio output over DisplayPort/HDMI to my TV is not  working. PulseAudio Mixer only shows "Internal Audio Analog Stereo" and sound is coming from the internal speaker.

I ran the ALSA Info Script with the following output: [http://www.alsa-project.org/db/?f=5c4bfcd51d504e19d0de68d04ae58fb76f07d826](http://www.alsa-project.org/db/?f=5c4bfcd51d504e19d0de68d04ae58fb76f07d826)

If you need more information, please tell me! Thank you very much for your help!
Pascal

---

### Post by Yellow Pasque on 2014-05-19
What GPU does it have?
```
lspci -k
```

---

### Post by Pascal_Jerney on 2014-05-20
Hi Temüjin

> **Temüjin said:**
> What GPU does it have?


The output of lspci -k is:
```

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: i915
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3648
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: mei_me
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: ata_generic
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: serial
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: e1000e
00:1a.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: ehci-pci
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
    Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: ehci-pci
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: lpc_ich
00:1f.2 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 4-port SATA IDE Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: ata_piix
00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 3648
    Kernel driver in use: ata_piix

```

Regards
Pascal

---

