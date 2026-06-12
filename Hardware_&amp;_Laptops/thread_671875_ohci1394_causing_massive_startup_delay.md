---
title: "ohci1394 causing massive startup delay"
date: 2008-01-19
forum: Hardware &amp; Laptops
---

### Post by sdrawkcaBdepyTI on 2008-01-19
Alright, so I took great pains to convince my parents to switch their computer to Ubuntu after they had a horrible experience with Vista. Now the boot process is taking about 2 or 3 minutes. I looked at dmesg and found that there are a couple hundred messages to the effect of:
[    7.664000] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]

Here is a slightly larger chunk of the output:
[    8.260000] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[    8.360000] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[    8.460000] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[    8.556000] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[    8.556000] ohci1394: fw-host0: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[    8.556000] ACPI: Unable to derive IRQ for device 0000:01:01.0
[    8.560000] ACPI: PCI Interrupt 0000:01:01.0[A]: no GSI - using IRQ 5
[    8.708000] ohci1394: fw-host1: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    8.708000] ohci1394: fw-host1: OHCI-1394 0.0 (PCI): IRQ=[5]  MMIO=[fdf9d000-fdf9d7ff]  Max Packet=[2]  IR/IT contexts=[0/0]
[    8.808000] ohci1394: fw-host1: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    8.808000] ohci1394: fw-host1: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[    8.808000] ACPI: Unable to derive IRQ for device 0000:01:02.0
[    8.808000] ACPI: PCI Interrupt 0000:01:02.0[A]: no GSI - using IRQ 5
[    8.856000] ohci1394: fw-host2: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    8.956000] ohci1394: fw-host2: OHCI-1394 0.0 (PCI): IRQ=[5]  MMIO=[fdf9e000-fdf9e7ff]  Max Packet=[2]  IR/IT contexts=[0/0]
[    8.956000] ohci1394: fw-host2: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    9.056000] ohci1394: fw-host2: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[    9.056000] ACPI: Unable to derive IRQ for device 0000:01:03.0
[    9.056000] ACPI: PCI Interrupt 0000:01:03.0[A]: no GSI - using IRQ 5
[    9.104000] ohci1394: fw-host3: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    9.204000] ohci1394: fw-host3: OHCI-1394 0.0 (PCI): IRQ=[5]  MMIO=[fdf9f000-fdf9f7ff]  Max Packet=[2]  IR/IT contexts=[0/0]
[    9.204000] ohci1394: fw-host3: Get PHY Reg timeout [0x00000000/0x00000000/100]
[    9.304000] ohci1394: fw-host3: Serial EEPROM has suspicious values, attempting to set max_packet_size to 512 bytes
[    9.304000] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [APCM] -> GSI 23 (level, low) -> IRQ 16
[    9.452000] ohci1394: fw-host4: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[    9.612000] ohci1394: fw-host4: Runaway loop while stopping context: ...
[    9.672000] ohci1394: fw-host4: Runaway loop while stopping context: ...
[    9.708000] irq 5: nobody cared (try booting with the "irqpoll" option)
[    9.708000]  [<c015b594>] __report_bad_irq+0x24/0x80
[    9.708000]  [<c015b852>] note_interrupt+0x262/0x2a0
[    9.708000]  [<c015aab0>] handle_IRQ_event+0x30/0x60
[    9.708000]  [<c015c23b>] handle_fasteoi_irq+0xbb/0xf0
[    9.708000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[    9.708000]  [<c0105223>] common_interrupt+0x23/0x30



I have no idea what to do with this, and I haven't seen anything that matches it on the forum either (at least in terms of the number of timeout messages - it does them for fw-host0 through fw-host30). 

I tried adding ohci1394 to the blacklist but the problem persisted after reboot. I'm comfortable with the command line and know a couple tricks but overall I'm kind of new to linux and so I don't know all the useful commands and file locations yet!

Here is a (long) excerpt from dmesg showing everything from the start of booting through a couple cycles of this PHY timeout stuff to give a flavor of what's going on. 

The complete dmesg file was a bit long to paste onto the page, but I've added it as an attachment. 

My parents don't even need any firewire capabilities, so if it has to be disabled to fix the problem that's not a problem! 
Please help  - I don't want them to switch back after I've spent so much time pitching Ubuntu to them!


Thanks,
Brian

---

### Post by sdrawkcaBdepyTI on 2008-01-19
I disabled firewire through the BIOS, and now booting in 20 seconds with no mess of error messages at boot time :). So things aren't nearly as urgent now. That being said, if anyone has any suggestions on how I could dig a little deeper and figure out what's going on here, maybe figure out a workaround, I'd be happy to put in the footwork.

---

### Post by ewy on 2008-01-19
I had a similar problem with an HP Compaq nx6130 laptop trying to run Gutsy 7.10. 

My message was along the lines of 
ohci1394: fw-host0: Unrecoverable Error

That came after loads of transmit failed messages. Even after figuring out that I could hold the power button on the laptop case down for a few seconds and then release to break the ohci1394 loop, my system would freeze unpredictably.

Unfortunately I could not find a setting in my BIOS for disabling the 1394 interface, so I scrapped Gutsy and I'm installing XP. I'm having intermittent freeze problems in XP too, so I fear my motherboard is somehow damaged, though I have no idea how to find out.

Anyone know how to disable 1394 or troubleshoot it (or other motherboard problems) from Ubuntu?

Cheers.

---

### Post by mazamazine on 2008-05-21
I GOT THE ANSWER !!!!
Yeeeeah !!

You have to blacklist ohci1394, ieee1394 and sbp2 in
/etc/modprobe.d/blacklist :

```
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
blacklist ohci1394
blacklist ieee1394
blacklist sbp2
```

---

### Post by mazamazine on 2008-05-21
I spoke a bit fast I guess... It did it again but after many "normal" boot...
Strange

---

### Post by mazamazine on 2008-05-29
Maybe new answers through adding irqpoll
follow : [http://ubuntuforums.org/showthread.php?t=810125](http://ubuntuforums.org/showthread.php?t=810125)

---

