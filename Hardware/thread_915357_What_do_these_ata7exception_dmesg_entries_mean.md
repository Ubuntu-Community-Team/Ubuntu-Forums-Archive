---
title: "What do these ata7/exception dmesg entries mean?"
date: 2008-09-09
forum: Hardware
---

### Post by Ralf Brauer on 2008-09-09
Hi,

I wonder if these entries mean something bad about my disk. It is an old 40 GB IDE Seagate hard disk.

The complete dmesg file is here: [http://paste.ubuntu.com/45089/](http://paste.ubuntu.com/45089/)

[   41.895969] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[   41.896958] pata_amd 0000:00:06.0: version 0.3.10
[   41.896999] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   41.898985] scsi6 : pata_amd
[   41.899491] scsi7 : pata_amd
[   41.900099] ata7: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xe000 irq 14
[   41.900102] ata8: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xe008 irq 15
[   42.072235] ata7.00: ATA-6: ST340810A, 3.34, max UDMA/100
[   42.072240] ata7.00: 78165360 sectors, multi 16: LBA 
[   42.111992] ata7.00: configured for UDMA/100
[   42.282469] scsi 6:0:0:0: Direct-Access     ATA      ST340810A        3.34 PQ: 0 ANSI: 5
[   42.282811] sd 6:0:0:0: [sdf] 78165360 512-byte hardware sectors (40021 MB)
[   42.282822] sd 6:0:0:0: [sdf] Write Protect is off
[   42.282825] sd 6:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   42.282841] sd 6:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.282888] sd 6:0:0:0: [sdf] 78165360 512-byte hardware sectors (40021 MB)
[   42.282897] sd 6:0:0:0: [sdf] Write Protect is off
[   42.282899] sd 6:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   42.282914] sd 6:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   42.282917]  sdf: sdf1 sdf2
[   42.306236] sd 6:0:0:0: [sdf] Attached SCSI disk
[   42.306266] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   47.782996] kjournald starting.  Commit interval 5 seconds
[   47.783012] EXT3-fs: mounted filesystem with ordered data mode.
[   48.275704] ata7.00: [COLOR="Red"]exception [/COLOR]Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   48.275755] ata7.00: BMDMA stat 0x64
[   48.275799] ata7.00: cmd c8/00:78:63:00:78/00:00:00:00:00/e4 tag 0 dma 61440 in
[   48.275800]          res 51/84:00:63:00:78/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
[   48.275847] ata7.00: status: { DRDY ERR }
[   48.275887] ata7.00: error: { ICRC ABRT }
[   48.275945] ata7: soft resetting link
[   48.487163] ata7.00: configured for UDMA/100
[   48.487170] ata7: EH complete
[   48.776897] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   48.776942] ata7.00: BMDMA stat 0x64
[   48.776984] ata7.00: cmd c8/00:78:63:00:78/00:00:00:00:00/e4 tag 0 dma 61440 in
[   48.776985]          res 51/84:00:63:00:78/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
[   48.777031] ata7.00: status: { DRDY ERR }
[   48.777071] ata7.00: error: { ICRC ABRT }
[   48.777121] ata7: soft resetting link
[   48.996776] ata7.00: configured for UDMA/100
[   48.996780] ata7: EH complete
[   49.322609] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   49.322653] ata7.00: BMDMA stat 0x64
[   49.322695] ata7.00: cmd c8/00:78:63:00:78/00:00:00:00:00/e4 tag 0 dma 61440 in
[   49.322696]          res 51/84:00:63:00:78/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
[   49.322743] ata7.00: status: { DRDY ERR }
[   49.322783] ata7.00: error: { ICRC ABRT }
[   49.322831] ata7: soft resetting link
[   49.536384] ata7.00: configured for UDMA/100
[   49.536388] ata7: EH complete
[   49.842595] ata7.00: limiting speed to UDMA/66:PIO4
[   49.842597] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   49.842642] ata7.00: BMDMA stat 0x64
[   49.842684] ata7.00: cmd c8/00:78:63:00:78/00:00:00:00:00/e4 tag 0 dma 61440 in
[   49.842685]          res 51/84:00:63:00:78/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
[   49.842732] ata7.00: status: { DRDY ERR }
[   49.842784] ata7.00: error: { ICRC ABRT }
[   49.842846] ata7: soft resetting link
[   50.055984] ata7.00: configured for UDMA/66
[   50.055988] ata7: EH complete
[   50.362813] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   50.362870] ata7.00: BMDMA stat 0x64
[   50.362925] ata7.00: cmd c8/00:78:63:00:78/00:00:00:00:00/e4 tag 0 dma 61440 in
[   50.362927]          res 51/84:00:63:00:78/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
[   50.362999] ata7.00: status: { DRDY ERR }
[   50.363051] ata7.00: error: { ICRC ABRT }
[   50.363113] ata7: soft resetting link
[   50.575585] ata7.00: configured for UDMA/66
[   50.575588] ata7: EH complete
[   50.884153] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   50.884211] ata7.00: BMDMA stat 0x64
[   50.884266] ata7.00: cmd c8/00:78:63:00:78/00:00:00:00:00/e4 tag 0 dma 61440 in
[   50.884267]          res 51/84:00:63:00:78/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
[   50.884340] ata7.00: status: { DRDY ERR }
[   50.884393] ata7.00: error: { ICRC ABRT }
[   50.884454] ata7: soft resetting link
[   51.095193] ata7.00: configured for UDMA/66
[   51.095198] sd 6:0:0:0: [sdf] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[   51.095202] sd 6:0:0:0: [sdf] Sense Key : Aborted Command [current] [descriptor]
[   51.095206] Descriptor sense data with sense descriptors (in hex):
[   51.095208]         72 0b 47 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
[   51.095213]         04 78 00 63 
[   51.095216] sd 6:0:0:0: [sdf] Add. Sense: Scsi parity error
[   51.095222] end_request: I/O error, dev sdf, sector 74973283
[   51.095227] ata7: EH complete
[   51.095246] sd 6:0:0:0: [sdf] 78165360 512-byte hardware sectors (40021 MB)
[   51.095257] sd 6:0:0:0: [sdf] Write Protect is off
[   51.095259] sd 6:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   51.095275] sd 6:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   51.095290] sd 6:0:0:0: [sdf] 78165360 512-byte hardware sectors (40021 MB)
[   51.095298] sd 6:0:0:0: [sdf] Write Protect is off
[   51.095300] sd 6:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[   51.095314] sd 6:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   51.424378] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   51.424436] ata7.00: BMDMA stat 0x64
[   51.424491] ata7.00: cmd c8/00:08:d3:00:78/00:00:00:00:00/e4 tag 0 dma 4096 in
[   51.424492]          res 51/84:00:d3:00:78/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
[   51.424565] ata7.00: status: { DRDY ERR }
[   51.424621] ata7.00: error: { ICRC ABRT }
[   51.424683] ata7: soft resetting link
[   51.644784] ata7.00: configured for UDMA/66
[   51.644788] ata7: EH complete
[   51.967647] ata7.00: limiting speed to UDMA/33:PIO4
[   51.967649] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[   51.967707] ata7.00: BMDMA stat 0x64
[   51.967762] ata7.00: cmd c8/00:08:d3:00:78/00:00:00:00:00/e4 tag 0 dma 4096 in
[   51.967763]          res 51/84:00:d3:00:78/00:00:00:00:00/e4 Emask 0x10 (ATA bus error)
[   51.967835] ata7.00: status: { DRDY ERR }
[   51.967888] ata7.00: error: { ICRC ABRT }
[   51.967950] ata7: soft resetting link
[   52.184398] ata7.00: configured for UDMA/33
[   52.184402] ata7: EH complete

I wonder if it is just the normal process of the system finding out how fast the drive is, or is this a sign for problems?


This is the Seagate page for the drive:

[http://www.seagate.com/ww/v/index.jsp?vgnextoid=fffb5a802efbd010VgnVCM100000dd04090aRCRD&locale=en-US&capacity=&reqPage=Legacy&prodfinder_button=1&model_number=ST340810A&interfaces=&product_select=all_product](http://www.seagate.com/ww/v/index.jsp?vgnextoid=fffb5a802efbd010VgnVCM100000dd04090aRCRD&locale=en-US&capacity=&reqPage=Legacy&prodfinder_button=1&model_number=ST340810A&interfaces=&product_select=all_product)

The system is a hardy 32 bit on a amd64 cpu. 1gb ram

Please ask I can provide more infos.

Thank you
Ralf

---

### Post by mrsteveman1 on 2008-09-09
First i would check the cable, make sure its the flat ribbon kind no more than a few inches long, sometimes the longer, round kind gives errors because they are out of spec.

There is a sector error there, so check what SMART says:

```

sudo smartctl -H /dev/sdf
```

This should give you a quick response as to SMART finding anything bad in the past or now.

Also do:

```
sudo smartctl -A /dev/sdf
```

post the values table that it gives you, you should be able to see though if there are a lot of some specific errors. 

Probably a good idea to have SMART run an extended selftest on the drive anyway:

```
sudo smartctl --test=long -C /dev/sdf
```

This will run the extended selftest, and it will tell you how long it takes. When it is done you can get the results like this:

```
sudo smartctl --log=selftest /dev/sdf
```

---

### Post by Ralf Brauer on 2008-09-10
Steve, your information is of great value for me. I installed smartmontools which contain smartctl:

```
sudo aptitude install smartmontools
```

The first test:

```
sudo smartctl -H /dev/sdf
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

```

I have a non standard long flat cable, I will get a new cable which is shorter and then post the results again. Here is what the second test says with the long cable anyway:


```
sudo smartctl -A /dev/sdf
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   064   053   025    Pre-fail  Always       -       99841486
  3 Spin_Up_Time            0x0003   099   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       550
  5 Reallocated_Sector_Ct   0x0033   099   099   036    Pre-fail  Always       -       14
  7 Seek_Error_Rate         0x000f   080   060   030    Pre-fail  Always       -       112575438
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       5572
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1337
194 Temperature_Celsius     0x0022   043   048   000    Old_age   Always       -       43
195 Hardware_ECC_Recovered  0x001a   100   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   192   000    Old_age   Always       -       24
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

```

I will do the rest of the tests with the new cable tomorrow.

Thank you very much!

---

### Post by mrsteveman1 on 2008-09-10
I don't see any pending sectors, but there are 14 reallocated ones i think.

Something I always do periodically though (in addition to the long selftest i listed above) is to write zeros to the entire device like this:

```
sudo dd if=/dev/zero of=/dev/sdX bs=5M
```

If the drive already knows about bad sectors, a write to those sectors gives the drive a chance to reallocate them. If it doesn't know about them yet, a write to every sector will certainly find them.

---

### Post by Ralf Brauer on 2008-09-15
After replacing the cable there were still error messages.

In the meantime I decided to buy a 1000 GB hard drive and to replace the drive in question and also some of my too many smaller drives. I need the machine urgently, and this seemed an overall reasonable solution for me. 

So please forgive that I did not take the time and do all the tests again from the beginning, i decided to not use the drive any more and labelled it "suspicious / errors" and put it away.

But I learned a lot from this thread, e.g. about smartmontools,  and hopefully others will find it useful too. (I am not marking it as solved but is there some adequate procedure?)

Also the `writing zeroes` is really helpful. I always knew that just quick formating a drive before using it in a new setup is not enough, but I did not know better.

Thank you very much for your great assistance in "times of panic", mrsteveman1 ! When I started this thead I was not even sure if the messages weren't just indicating the normal boot procedure for such an old drive.

---

