---
title: "Still can't get headphone jack to work :( ALC262"
date: 2009-09-20
forum: Hardware
---

### Post by avelis26 on 2009-09-20
Ok, I've searched and searched and tried many different solutions but still unable to get any output from my headphone jack. PLEASE HELP.

I've tried modifying my ALSA base conf file with so many versions my head is going to explode.

Can someone work with me on this and help me to get my headphone jack to output SOMETHING. I hate windows, love Ubuntu. Running 9.04 btw.

aplay -l output
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Below is the output of dmesg or at least the parts that seem remotely related my audio card.

[   25.304809] pcmcia 0.0: pcmcia: registering new device pcmcia0.0
[   25.445516] 0.0: ttyS0 at I/O 0xf3f8 (irq = 3) is a 16450
[   25.476298] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   25.476395] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.500485] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   25.502445] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.503241] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   25.503915] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   25.504759] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   25.515235] hda_codec: Unknown model for ALC262, trying auto-probe from BIOS...
[   25.515821] hda_codec: Cannot set up configuration from BIOS.  Using base mode...
[43274.952371] ata_piix 0000:00:1f.1: PCI INT A disabled
[43274.952583] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[43274.968176] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[43274.968249] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[43274.968324] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[43275.016117] HDA Intel 0000:00:1b.0: PCI INT A disabled
[43275.032214] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[43276.584079] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[43276.584086] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[43276.600153] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[43276.600164] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[43276.600202] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[43276.600212] HDA Intel 0000:00:1b.0: setting latency timer to 64

---

### Post by Yellow Pasque on 2009-09-21
Upgrade to the latest ALSA and try the different model keyword in alsa-base: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

If you still can't get it working, follow the suggestions in that thread on reporting bugs to the ALSA developers. Good luck.

---

### Post by avelis26 on 2009-09-21
Thank god, fixed. All I did was run that upgrade script and reinstall ALSA and now works perfectly without any other mods. Thanks so much.

---

