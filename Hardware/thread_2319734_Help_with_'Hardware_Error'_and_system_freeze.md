---
title: "Help with 'Hardware Error' and system freeze?"
date: 2016-04-06
forum: Hardware
---

### Post by nadamsieee on 2016-04-06
My system randomly freezes, and today I discovered these messages in syslog:

```
Apr  6 15:47:19 neredium kernel: [  301.323443] [Hardware Error]: Corrected error, no action required.
Apr  6 15:47:19 neredium kernel: [  301.323448] [Hardware Error]: CPU:3 (15:2:0) MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc25405000040136
Apr  6 15:47:19 neredium kernel: [  301.323450] [Hardware Error]: MC2 Error Address: 0x00000007a16bc838
Apr  6 15:47:19 neredium kernel: [  301.323451] [Hardware Error]: MC2 Error: Fill ECC error on data fills.
Apr  6 15:47:19 neredium kernel: [  301.323453] [Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
Apr  6 15:47:19 neredium kernel: [  301.323456] mce: [Hardware Error]: Machine check events logged
Apr  6 15:47:20 neredium kernel: [  301.335382] [Hardware Error]: Corrected error, no action required.
Apr  6 15:47:20 neredium kernel: [  301.335388] [Hardware Error]: CPU:2 (15:2:0) MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc25405000040136
Apr  6 15:47:20 neredium kernel: [  301.335391] [Hardware Error]: MC2 Error Address: 0x00000007a16bc838
Apr  6 15:47:20 neredium kernel: [  301.335392] [Hardware Error]: MC2 Error: Fill ECC error on data fills.
Apr  6 15:47:20 neredium kernel: [  301.335394] [Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
Apr  6 15:47:20 neredium kernel: [  301.335397] mce: [Hardware Error]: Machine check events logged
Apr  6 15:49:49 neredium kernel: [  451.232316] [Hardware Error]: Corrected error, no action required.
Apr  6 15:49:49 neredium kernel: [  451.232322] [Hardware Error]: CPU:3 (15:2:0) MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc2540a000040136
Apr  6 15:49:49 neredium kernel: [  451.232326] [Hardware Error]: MC2 Error Address: 0x00000007f475fd38
Apr  6 15:49:49 neredium kernel: [  451.232327] [Hardware Error]: MC2 Error: Fill ECC error on data fills.
Apr  6 15:49:49 neredium kernel: [  451.232329] [Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
Apr  6 15:49:49 neredium kernel: [  451.232332] mce: [Hardware Error]: Machine check events logged
Apr  6 15:49:50 neredium kernel: [  451.244297] [Hardware Error]: Corrected error, no action required.
Apr  6 15:49:50 neredium kernel: [  451.244303] [Hardware Error]: CPU:2 (15:2:0) MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc2540c000040136
Apr  6 15:49:50 neredium kernel: [  451.244306] [Hardware Error]: MC2 Error Address: 0x00000007ab43e638
Apr  6 15:49:50 neredium kernel: [  451.244307] [Hardware Error]: MC2 Error: Fill ECC error on data fills.
Apr  6 15:49:50 neredium kernel: [  451.244309] [Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
Apr  6 15:49:50 neredium kernel: [  451.244312] mce: [Hardware Error]: Machine check events logged
Apr  6 15:52:19 neredium kernel: [  600.178290] [Hardware Error]: Corrected error, no action required.
Apr  6 15:52:19 neredium kernel: [  600.178295] [Hardware Error]: CPU:0 (15:2:0) MC2_STATUS[-|CE|MiscV|-|-|-|-|CECC]: 0x98254000000c0176
Apr  6 15:52:19 neredium kernel: [  600.178298] [Hardware Error]: MC2 Error: VB Data ECC or parity error.
Apr  6 15:52:19 neredium kernel: [  600.178300] [Hardware Error]: cache level: L2, tx: DATA, mem-tx: EV
Apr  6 15:52:19 neredium kernel: [  600.178303] mce: [Hardware Error]: Machine check events logged
Apr  6 15:53:34 neredium kernel: [  676.091771] [Hardware Error]: Corrected error, no action required.
Apr  6 15:53:34 neredium kernel: [  676.091776] [Hardware Error]: CPU:3 (15:2:0) MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc254000000a0145
Apr  6 15:53:34 neredium kernel: [  676.091779] [Hardware Error]: MC2 Error Address: 0x00000000000001c0
Apr  6 15:53:34 neredium kernel: [  676.091781] [Hardware Error]: MC2 Error: WCC Data ECC error.
Apr  6 15:53:34 neredium kernel: [  676.091783] [Hardware Error]: cache level: L1, tx: DATA, mem-tx: DWR
Apr  6 15:53:34 neredium kernel: [  676.091786] mce: [Hardware Error]: Machine check events logged
Apr  6 15:53:35 neredium kernel: [  676.103764] [Hardware Error]: Corrected error, no action required.
Apr  6 15:53:35 neredium kernel: [  676.103770] [Hardware Error]: CPU:2 (15:2:0) MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc25404000040136
Apr  6 15:53:35 neredium kernel: [  676.103774] [Hardware Error]: MC2 Error Address: 0x00000007b1cb8038
Apr  6 15:53:35 neredium kernel: [  676.103775] [Hardware Error]: MC2 Error: Fill ECC error on data fills.
Apr  6 15:53:35 neredium kernel: [  676.103777] [Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
Apr  6 15:54:50 neredium kernel: [  751.059603] [Hardware Error]: Corrected error, no action required.
Apr  6 15:54:50 neredium kernel: [  751.059607] [Hardware Error]: CPU:2 (15:2:0) MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc25401000040136
Apr  6 15:54:50 neredium kernel: [  751.059610] [Hardware Error]: MC2 Error Address: 0x000000078d6bd798
Apr  6 15:54:50 neredium kernel: [  751.059611] [Hardware Error]: MC2 Error: Fill ECC error on data fills.
Apr  6 15:54:50 neredium kernel: [  751.059612] [Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
Apr  6 15:54:50 neredium kernel: [  751.059616] mce: [Hardware Error]: Machine check events logged
Apr  6 15:57:19 neredium kernel: [  900.937208] [Hardware Error]: Corrected error, no action required.
Apr  6 15:57:19 neredium kernel: [  900.937213] [Hardware Error]: CPU:3 (15:2:0) MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc254020000a0145
Apr  6 15:57:19 neredium kernel: [  900.937216] [Hardware Error]: MC2 Error Address: 0x0000000000000180
Apr  6 15:57:19 neredium kernel: [  900.937217] [Hardware Error]: MC2 Error: WCC Data ECC error.
Apr  6 15:57:19 neredium kernel: [  900.937219] [Hardware Error]: cache level: L1, tx: DATA, mem-tx: DWR
Apr  6 15:57:19 neredium kernel: [  900.937222] mce: [Hardware Error]: Machine check events logged
```

The cpu is an AMD FX(tm)-9590 Eight-Core Processor, and there are 32GB of RAM.

Any help debugging this?

---

### Post by Chuck_McManis on 2016-04-06
You need to replace your memory. You're seeing a lot of ECC errors which are typical of memory that is failing. I'm guessing that at some point you get an uncorrectable multibit error. If you have an IPMI controller/card you can probably dump the last machine check error (MCE) from its buffer (it would have been written to the SM Bus).
--Chuck

---

### Post by Yellow Pasque on 2016-04-08
^That would be my guess, since the errors are coming from different cores and cache levels.
Memtest should help pinpoint which RAM modules are defective.

---

### Post by nadamsieee on 2016-06-22
I replaced the RAM (link below) and re-ran memtest overnight.

No errors were found.

I still get random system freezes. :(

[http://www.crucial.com/usa/en/crosshair-v-formula-z/CT3684739](http://www.crucial.com/usa/en/crosshair-v-formula-z/CT3684739)

---

### Post by nadamsieee on 2016-06-25
Same story after replacing the video card.

I am running out of hardware to swap out (an expensive process), and the error messages in the original post are not consistent with the freezing issue.

---

