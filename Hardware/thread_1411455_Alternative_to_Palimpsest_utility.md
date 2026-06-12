---
title: "Alternative to Palimpsest utility?"
date: 2010-02-20
forum: Hardware
---

### Post by hxcobd on 2010-02-20
I recently threw an IBM/Lenovo (Samsung, actually) brand SSD in my Thinkpad X41, and upon boot, Palimpsest reported it had some appallingly high number of bad sectors... Something equalling roughly 3.7 gigs or so.

I know this to be untrue, and have read a number of posts/threads on false positives from Palimpsest, especially with this model hard drive. (Also, the drive is brand new and has never been used.)

Anyone know of a good alternative to Palimpsest for checking for bad sectors and such, so I can do a VALID scan of this drive?

---

### Post by hxcobd on 2010-02-20
Bump?

---

### Post by hugmenot on 2010-02-21
Can you install libatasmart-bin and post the output from

```
sudo skdump /dev/sdX
```

with X being your SSD.

---

### Post by hugmenot on 2010-02-21
This is what I get. I patched libatasmart to also display attributes 175 through 183. Those are (Samsung) SSD specific. I got the meaning of these attributes from [Samsung Semiconductor]("http://www.samsung.com/global/business/semiconductor/products/flash/ssd/2008/down/pm410_18_sata_ii_spec_10.pdf"). And [technical specs]("http://www.samsung.com/global/business/semiconductor/products/flash/ssd/2008/product/pcLineup.html") of other Samsung SSDs.



```
$ sudo skdump /dev/sda
Device: sat16:/dev/sda
Type: 16 Byte SCSI ATA SAT Passthru
Size: 122104 MiB
Model: [SAMSUNG MMCQE28G8MUP-0VA]
Serial: [SE837A6888]
Firmware: [VAM0DL1Q]
SMART Available: yes
Quirks:
Awake: yes
SMART Disk Health Good: yes
Off-line Data Collection Status: [Off-line data collection activity was completed without error.]
Total Time To Complete Off-Line Data Collection: 360 s
Self-Test Execution Status: [The previous self-test routine completed without error or no self-test has ever been run.]
Percent Self-Test Remaining: 0%
Conveyance Self-Test Available: no
Short/Extended Self-Test Available: yes
Start Self-Test Available: yes
Abort Self-Test Available: yes
Short Self-Test Polling Time: 6 min
Extended Self-Test Polling Time: 36 min
Conveyance Self-Test Polling Time: 0 min
Bad Sectors: No such file or directory
Powered On: 6.5 months
Power Cycles: 929
Average Powered On Per Power Cycle: 5.0 h
Temperature: No such file or directory
Attribute Parsing Verification: Good
Overall Status: GOOD
ID# Name                        Value Worst Thres Pretty      Raw            Type    Updates Good Good/Past
  9 power-on-hours               99    99     0   6.5 months  0x481200000000 old-age online  n/a  n/a 
 12 power-cycle-count            99    99     0   929         0xa10300000000 old-age online  n/a  n/a 
175 program-fail-count-chip     100   100    11   0           0x000000000000 old-age online  yes  yes 
176 erase-fail-count-chip       100   100    11   0           0x000000000000 old-age online  yes  yes 
177 wear-leveling-count          99    99    23   330         0x4a0100000000 prefail online  yes  yes 
178 used-reserved-blocks-chip    91    91    11   10          0x0a0000000000 prefail online  yes  yes 
179 used-reserved-blocks-total   98    98    10   53          0x350000000000 prefail online  yes  yes 
180 unused-reserved-blocks       98    98    10   3851        0x0b0f00000000 prefail online  yes  yes 
181 program-fail-count-total    100   100    10   0           0x000000000000 old-age online  yes  yes 
182 erase-fail-count-total      100   100    10   0           0x000000000000 old-age online  yes  yes 
183 runtime-bad-blk-total       100   100    10   0           0x000000000000 prefail online  yes  yes 
187 reported-uncorrect          100   100     0   0 sectors   0x000000000000 prefail online  n/a  n/a 
195 hardware-ecc-recovered      200   200     0   0           0x000000000000 old-age online  n/a  n/a 
198 offline-uncorrectable       100   100     0   0 sectors   0x000000000000 old-age offline n/a  n/a 
199 udma-crc-error-count        253   253     0   0           0x000000000000 old-age online  n/a  n/a 
233 power-on-seconds-2          199   199     0   n/a         0x4ffa02000000 old-age online  n/a  n/a 
234 uncorrectable-ecc-count     100   100     0   0 sectors   0x000000000000 old-age online  n/a  n/a 
235 good-block-rate             100   100     0   n/a         0x000000000000 old-age online  n/a  n/a 
236 attribute-236                99    99     0   n/a         0x670000000000 old-age online  n/a  n/a 
237 attribute-237                99    99     0   n/a         0x150200000000 old-age online  n/a  n/a 
238 attribute-238               100   100     0   n/a         0x000000000000 old-age online  n/a  n/a 
```

---

