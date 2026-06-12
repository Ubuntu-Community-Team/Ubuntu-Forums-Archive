---
title: "Lucid DVD problem"
date: 2011-01-15
forum: Hardware
---

### Post by x53x6ex69x67x67x65x72 on 2011-01-15
Hi
My DVD drive doesn't recognize/load all DVD types (it loads some of them and doesn't load some others)
My drive info:
```

description: DVD-RAM writer
product: DVD+-RW GT10N
vendor: HL-DT-ST
physical id: 1
bus info: scsi@1:0.0.0
logical name: /dev/cdrom
logical name: /dev/cdrw
logical name: /dev/dvd
logical name: /dev/dvdrw
logical name: /dev/scd0
logical name: /dev/sr0
version: A105
capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
configuration: ansiversion=5 status=nodisc

```when I insert DVDs that fail "dmesg|tail" reports:
```
[ 4391.113655] sr 1:0:0:0: [sr0] Unhandled sense code
[ 4391.113658] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4391.113662] sr 1:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 4391.113666] sr 1:0:0:0: [sr0] Add. Sense: Cannot read medium - unknown format
[ 4391.113671] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 4391.113680] end_request: I/O error, dev sr0, sector 0

```What's the problem ? 
what is the solution?

---

### Post by x53x6ex69x67x67x65x72 on 2011-01-18
bump

---

### Post by mc4man on 2011-01-18
Maybe take a look at this thread, starting here should be enough.

Fairly simple atm - if the 'not loaded' media is detected then you should be able to make use of, whether a data dvd or DVD Movie disk.
(whether the file system is auto mounted or mounted at all doesn't really matter

If the media is not detected then there is nothing to be done till it is detected.

[http://ubuntuforums.org/showthread.php?p=10343732#post10343732](http://ubuntuforums.org/showthread.php?p=10343732#post10343732)

---

