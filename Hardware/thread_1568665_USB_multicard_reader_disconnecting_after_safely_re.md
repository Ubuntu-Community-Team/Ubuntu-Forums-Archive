---
title: "USB multicard reader disconnecting after safely remove"
date: 2010-09-05
forum: Hardware
---

### Post by NMFTM on 2010-09-05
I'm experiencing the same problem (or, maybe I should say "feature" as the guy in [this thread]("http://ubuntuforums.org/showthread.php?t=1410001") is. But his thread is seven months old and was using v9.10 while I'm using 10.04. I'm also using [this]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813998514&Tpk=FPM220") multicard reader.

A workaround could be to just take the device out without safely removing it. But I'm paranoid about delayed allocation errors.

Here is the my /var/log/syslog output for putting the SD card into my USB reader:
```
Sep  5 15:59:28 ben-u64 kernel: [   81.164436] sd 10:0:0:0: [sdb] 990976 512-byte logical blocks: (507 MB/483 MiB)
Sep  5 15:59:28 ben-u64 kernel: [   81.164629] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
Sep  5 15:59:28 ben-u64 kernel: [   81.165079] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Sep  5 15:59:28 ben-u64 kernel: [   81.165681] xhci_hcd 0000:06:00.0: WARN: Stalled endpoint
Sep  5 15:59:28 ben-u64 kernel: [   81.166077] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Sep  5 15:59:28 ben-u64 kernel: [   81.166079]  sdb: sdb1
```There was no output for using the eject or safely remove options.  Although, after going to the Disk Utility I no longer see my USB SD  reader. And trying to manually mount the SD card even though it's in and  the light on the reader is on results in an error message saying that  /dev/sdb doesn't exist.

The only apparent way to get the device back is to restart my computer.

---

### Post by jjbarrows on 2011-03-29
i'm using 10.10 and have two options
safely remove - removes the USB card reader (cant use till rebooted)
eject - finishes all writes and unmounts the individual card (re-insert and read fine)

I was using safely remove and getting frustrated (eject didnt seem to make sense, having used computers since the days of flopies that some machines could physically eject itself)

now i know better, would like to know how to get the hardware back without rebooting though

---

### Post by Ken Wood on 2011-09-04
Me too! Does that help at all?

---

