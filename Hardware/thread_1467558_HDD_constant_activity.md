---
title: "HDD constant activity"
date: 2010-04-30
forum: Hardware
---

### Post by half-life on 2010-04-30
My laptop hdd is always in constant activity, i checked on system log and looks like the hdd is always in loop error...

May  1 02:33:21 nuno-laptop kernel: [42071.381688] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  1 02:33:21 nuno-laptop kernel: [42071.412697] ata3.00: configured for PIO0
May  1 02:33:21 nuno-laptop kernel: [42071.413268] ata3: EH complete
May  1 02:33:28 nuno-laptop kernel: [42078.330064] ata3.00: qc timeout (cmd 0xa0)
May  1 02:33:28 nuno-laptop kernel: [42078.330083] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
May  1 02:33:28 nuno-laptop kernel: [42078.330089] ata3.00: irq_stat 0x40000001
May  1 02:33:28 nuno-laptop kernel: [42078.330095] sr 2:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
May  1 02:33:28 nuno-laptop kernel: [42078.330113] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
May  1 02:33:28 nuno-laptop kernel: [42078.330115]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
May  1 02:33:28 nuno-laptop kernel: [42078.330120] ata3.00: status: { DRDY ERR }
May  1 02:33:28 nuno-laptop kernel: [42078.330128] ata3: hard resetting link
May  1 02:33:28 nuno-laptop kernel: [42078.860049] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  1 02:33:28 nuno-laptop kernel: [42078.890790] ata3.00: configured for PIO0
May  1 02:33:28 nuno-laptop kernel: [42078.891342] ata3: EH complete
May  1 02:33:33 nuno-laptop kernel: [42083.912568] ata3.00: qc timeout (cmd 0xa0)
May  1 02:33:33 nuno-laptop kernel: [42083.912586] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
May  1 02:33:33 nuno-laptop kernel: [42083.912592] ata3.00: irq_stat 0x40000001
May  1 02:33:33 nuno-laptop kernel: [42083.912598] sr 2:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
May  1 02:33:33 nuno-laptop kernel: [42083.912616] ata3.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
May  1 02:33:33 nuno-laptop kernel: [42083.912617]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
May  1 02:33:33 nuno-laptop kernel: [42083.912622] ata3.00: status: { DRDY ERR }
May  1 02:33:33 nuno-laptop kernel: [42083.912630] ata3: hard resetting link
May  1 02:33:34 nuno-laptop kernel: [42084.440060] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
May  1 02:33:34 nuno-laptop kernel: [42084.469086] ata3.00: configured for PIO0
May  1 02:33:34 nuno-laptop kernel: [42084.471455] ata3: EH complete

Is always doing this
I'm using ubuntu 10.04 64bits
Laptop Acer 5737Z and already tried AHCI and IDE on bios, problem persists...

Some solution to this problem?

---

### Post by duke_peter on 2010-05-01
same problem here.
Laptop IBM R40

---

