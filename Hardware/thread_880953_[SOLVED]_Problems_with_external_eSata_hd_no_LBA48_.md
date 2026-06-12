---
title: "[SOLVED] Problems with external eSata hd: no LBA48 support???"
date: 2008-08-05
forum: Hardware
---

### Post by maxino on 2008-08-05
Hello all,

I just installed an eSata PCI controller card which seems to be recognized OK:

> maxino@netvista:~$ lspci

...snip...

02:0c.0 SATA controller: Initio Corporation INI-1623 PCI SATA-II Controller (rev 02)

However my new 500GB external eSata hd is not recognised by my system and it is not mapped to any device.
I noticed the following error in my dmesg output:

> maxino@netvista:~$ dmesg

...snip...

[   30.366687] sata_inic162x 0000:02:0c.0: version 0.3
[   30.366741] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 20
[   30.387783] scsi2 : sata_inic162x
[   30.388080] scsi3 : sata_inic162x
[   30.388127] ata3: SATA max UDMA/133 mmio m4096@0x96001000 port 0x96001000 cmd 0x3000 ctl 0x2c02 irq 20
[   30.388132] ata4: SATA max UDMA/133 mmio m4096@0x96001000 port 0x96001040 cmd 0x2800 ctl 0x2402 irq 20
[   30.879088] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.895281] ata3.00: HPA unlocked: 976773168 -> 976773168, native 61985760239664
[   30.895289] ata3.00: ATA-8: ST3500820AS, LC11, max UDMA/133
[   30.895293] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[COLOR="Red"][   30.895311] ata3.00: [COLOR="Red"]ERROR: This driver doesn't support LBA48 yet and may cause
[   30.895313]                 data corruption on such devices.  [/COLOR]Disabling.[/COLOR]
[   30.895318] ata3.00: disabled
[   31.230617] ata4: SATA link down (SStatus 0 SControl 300)

My understanding is that I miss this LBA48 support...
Googling around I found that it's something necessary for large drives but:

1. Why I don't have it? Something to do with my motherboard?
2. How can I solve this issue?

Thanks,

---

### Post by maxino on 2008-08-06
Hi all,

In the meantime I did some more homework and read other forums and came to the conclusion that the kernel driver for the chipset Initio fitted on my controller card is bugged and does not support LBA48.

Anyone with the same problem?
Anyone with some suggestion and/or solution?:)

Thanks a bunch,

---

### Post by maxino on 2008-08-09
...bump...?

---

### Post by maxino on 2008-08-12
Some progress on this issue...
I contacted the developer of the sata_inic162x.ko module and he told me that kernel 2.6.26 ships with a fixed version of such module (I think it's 0.4) which supports LBA48.
I found the source code for this module and now what I would like to do is compile it against my current kernel headers and libs (2.6.24-19-generic) and try it on my system.

Does somebody know how to do it?:)

Cheers,

---

### Post by maxino on 2008-08-13
Hi,
I decided to bite the bullet and compiled and installed a new kernel.
I am running now version 2.6.26.2.
My eSata hd is now recognized and automatically mounted and as far as I can tell works great.
Problem solved:)

Cheers

---

### Post by darkenergy on 2008-08-20
hi

i got nearly the same problem and also want to update the kernel but i'm not used to that.

what guide or how-to did you use?

it would be great to have this fixed... no longar anoying usb2 speed

---

### Post by maxino on 2008-08-30
Hi,

I followed these [[COLOR="Blue"]instructions[/COLOR]]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html") and worked for me.
But you can find info just as good (if not better) in the forum section "Tutorials and Tips" - look for the Master Kernel Thread.

Ciao

---

