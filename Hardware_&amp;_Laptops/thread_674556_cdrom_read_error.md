---
title: "cdrom read error"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by luzdegas on 2008-01-21
Hi.
I have a Dell XPS M1210 running Gutsy, and I've made a recently upgrade from Feisty.

I use to read CDs without any problems when I had Feisty. After the upgrade, I've started to have read error problems when reading CDs (this does not happen when I read DVDs, and they work ok). This is happening with CDs that I used to read fine with feisty. 

I usually try to read long avi files (about 700Mb), and when I have problems I try to copy the files to the hard drive. The weird thing is that the copy process stop after reading about 400Mb, with a "read error" message.

The ouput from dmesg is

```
[227841.943213] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[227841.943234] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[227841.943239] Info fld=0x57c6d
[227841.943241] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
[227841.943247] end_request: I/O error, dev sr0, sector 1438132
[227841.943251] Buffer I/O error on device sr0, logical block 359533
[227841.943256] Buffer I/O error on device sr0, logical block 359534
[227841.943260] Buffer I/O error on device sr0, logical block 359535
[227841.943263] Buffer I/O error on device sr0, logical block 359536
[227936.732214] npviewer.bin[25885]: segfault at 00000000ffffffec rip 00000000f7b3bb6f rsp 00000000ffafb140 error 6
[227973.975572] npviewer.bin[26150]: segfault at 00000000f77285da rip 00000000f7a29745 rsp 00000000f5acfc00 error 7
[228012.658400] npviewer.bin[26223]: segfault at 0000000000000039 rip 00000000f7aa919f rsp 00000000ffc96610 error 4
[228014.700408] npviewer.bin[26240]: segfault at 0000000000000001 rip 00000000f7ad96fe rsp 00000000f5b80c60 error 4
[228041.232856] npviewer.bin[26288]: segfault at 00000000f77285de rip 00000000f7a0a0ed rsp 00000000f5acfd80 error 7
[228043.274865] npviewer.bin[26271]: segfault at 0000000065786970 rip 00000000f779dba8 rsp 00000000ff89ba2c error 4
[228062.298208] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[228062.298219] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[228062.298227] Info fld=0x36c90
[228062.298230] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
[228062.298239] end_request: I/O error, dev sr0, sector 897600
[228062.298246] Buffer I/O error on device sr0, logical block 224400
[228062.298254] Buffer I/O error on device sr0, logical block 224401
[228062.298260] Buffer I/O error on device sr0, logical block 224402
[228062.298266] Buffer I/O error on device sr0, logical block 224403
[228062.298273] Buffer I/O error on device sr0, logical block 224404
[228062.298279] Buffer I/O error on device sr0, logical block 224405
[228062.298286] Buffer I/O error on device sr0, logical block 224406
[228062.298292] Buffer I/O error on device sr0, logical block 224407
[228062.298298] Buffer I/O error on device sr0, logical block 224408
[228062.298304] Buffer I/O error on device sr0, logical block 224409
[228064.004936] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[228064.004947] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[228064.004955] Info fld=0x36c90
[228064.004969] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
[228064.004975] end_request: I/O error, dev sr0, sector 897600
[228065.016768] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[228065.016779] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[228065.016786] Info fld=0x36c90
[228065.016789] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
[228065.016799] end_request: I/O error, dev sr0, sector 897600
[228066.028822] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[228066.028829] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[228066.028834] Info fld=0x36c90
[228066.028835] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
[228066.028840] end_request: I/O error, dev sr0, sector 897600
[228067.040978] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[228067.040989] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[228067.040997] Info fld=0x36c90
[228067.041000] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
[228067.041009] end_request: I/O error, dev sr0, sector 897600
[228068.053123] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[228068.053134] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[228068.053142] Info fld=0x36c90
[228068.053145] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
[228068.053155] end_request: I/O error, dev sr0, sector 897600
[228068.053161] printk: 40 messages suppressed.
[228068.053166] Buffer I/O error on device sr0, logical block 224400
[228069.128251] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[228069.128262] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current]
[228069.128270] Info fld=0x36c90
[228069.128273] sr 1:0:0:0: [sr0] Add. Sense: Unrecovered read error
[228069.128282] end_request: I/O error, dev sr0, sector 897600

```

Any help is welcome!

---

### Post by tramir on 2008-02-07
Similar problem here, with a Dell Inspiron 6000. If anybody has an idea, please let us know... Thanks!

---

### Post by sriliam on 2008-02-22
Hi everybody !
Same trouble too with my TSSTCorp ! (SH-203D) ==> Samsung copy.
I bet your wrong dvds are dualed layered, don't they ?
Try ide-cd : nothing.
Re-compile kernel without ide anymore : sata discs fine but dvd dual layer still I/O errored.
Module : ahci.
Don't know what to do now.
Still search. When I got the fix, i will post it.
Seemed to be quite simple because google answers are not numerous.
See ya.

---

### Post by janfsd on 2008-05-24
I get the same problem since upgrading to Hardy.
Here it is a related topic: [http://ubuntuforums.org/showthread.php?t=726656](http://ubuntuforums.org/showthread.php?t=726656)

---

