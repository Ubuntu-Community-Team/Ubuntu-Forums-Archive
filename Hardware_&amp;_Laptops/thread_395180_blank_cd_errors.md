---
title: "blank cd errors"
date: 2007-03-27
forum: Hardware &amp; Laptops
---

### Post by dbbolton on 2007-03-27
it's seems that i've read about this problem before, but i can't find a thread specific to my problem.

1. when i right click and iso > Burn to Disc, the normal dialogue box appears. when i click OK, the dialogue box disappears.

2. when i try to burn a project with GnomeBaker, it halts at 50% on "Calculating Disc Size", then the program crashes.

3. here is the output from 'dmesg' :


```
[17182800.800000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17182802.848000] hdc: status error: status=0x00 { }
[17182802.848000] ide: failed opcode was: unknown
[17182802.848000] hdc: status error: status=0x00 { }
[17182802.848000] ide: failed opcode was: unknown
[17182802.848000] hdc: status error: status=0x00 { }
[17182802.848000] ide: failed opcode was: unknown
[17182802.848000] hdc: status error: status=0x00 { }
[17182802.848000] ide: failed opcode was: unknown
[17182802.848000] hdc: DMA disabled
[17182802.896000] hdc: ATAPI reset complete
[17182802.896000] hdc: status error: status=0x00 { }
[17182802.896000] ide: failed opcode was: unknown
[17182802.896000] hdc: status error: status=0x00 { }
[17182802.896000] ide: failed opcode was: unknown
[17182802.896000] hdc: status error: status=0x00 { }
[17182802.896000] ide: failed opcode was: unknown
[17182802.896000] hdc: status error: status=0x00 { }
[17182802.896000] ide: failed opcode was: unknown
[17182802.944000] hdc: ATAPI reset complete
[17182802.944000] hdc: status error: status=0x00 { }
[17182802.944000] ide: failed opcode was: unknown

```

---

### Post by dbbolton on 2007-03-27
reboot fixed this.

---

