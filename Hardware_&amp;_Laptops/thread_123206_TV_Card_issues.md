---
title: "TV Card issues"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by stepper on 2006-01-29
The manual says the name of the card is S801T FM/TV Tuner card and now for the life of me I can't get this card to work in Ubuntu. Here are some details about the card:
lspci:
> 0000:00:0a.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
ivtv-detect:
> driver:   cx8800-0.0.5
card:     Leadtek Winfast 2000XP Expert, bus info PCI:0000:00:0a.0
           /dev/vbi0: VBI encoding (links: /dev/vbi)
         /dev/video0: YUV encoding
         /dev/radio0: Radio

dmesg:
> [4298559.906000] cx2388x v4l2 driver version 0.0.5 loaded
[4298559.911000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 20
[4298559.911000] CORE cx88[0]: subsystem: 0000:0000, board: Leadtek Winfast 2000XP Expert [card=5,insmod option]
[4298559.911000] TV tuner 44 at 0x1fe, Radio tuner -1 at 0x1fe
[4298560.055000] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[4298560.055000] cx88[0]: Leadtek eeprom invalid.
[4298560.060000] input: cx88 IR (Leadtek Winfast 2000XP as /class/input/input7
[4298560.060000] cx88[0]/0: found at 0000:00:0a.0, rev: 5, irq: 20, latency: 32, mmio: 0xda000000
[4298560.086000] tuner 0-0060: All bytes are equal. It is not a TEA5767
[4298560.086000] tuner 0-0060: chip found @ 0xc0 (cx88[0])
[4298560.093000] tuner 0-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[4298560.094000] tuner 0-0061: chip found @ 0xc2 (cx88[0])
[4298560.205000] cx88[0]/0: registered device video0 [v4l2]
[4298560.227000] cx88[0]/0: registered device vbi0
[4298560.251000] cx88[0]/0: registered device radio0

please help listen to the radio, TV viewing doesn't really matter.

---

