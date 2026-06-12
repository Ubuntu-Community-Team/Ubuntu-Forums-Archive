---
title: "[SOLVED] Hardy refers to hdrive devices by id, uuid, or path; where is sdx?"
date: 2008-10-02
forum: Hardware
---

### Post by guatebus on 2008-10-02
Hi, I know linux refers to devices in versions previous to Hardy as sdX and such.  I want to reference to my hard drive (would be sda or hda in previous releases) but my hardy lists no sdX or hdX devices, only lists drives as by-id, by-uuid, or by-path.  Can anyone explain this please?? I am a linux newbie, and have searched the forums for this but haven't found an appropriate thread.

Thnx in advance

):P

---

### Post by Yellow Pasque on 2008-10-02
Try:
```
sudo lshw -C disk -businfo
```
Output looks like:
```
Bus info          Device      Class       Description
=====================================================
scsi@0:0.0.0      /dev/sda    disk        320GB SAMSUNG HD321KJ
scsi@2:0.0.0      /dev/cdrom  disk        CDDVDW SH-S203B
scsi@4:0.0.0      /dev/sdb    disk        40GB WDC WD400BEVS-22

```

---

### Post by Patb on 2008-10-03
And to correlate /dev/sdX with that partition's UUID:
```
sudo blkid
```
Cheers, Pat

---

### Post by guatebus on 2008-10-03
Thanks Temüjin and Patb for your suggestions; I found that the drives are there as sdX.

---

