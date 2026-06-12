---
title: "Unable to detect Hitachi 2gb microdrive (iCN 650)"
date: 2009-02-14
forum: Hardware
---

### Post by chapman55k on 2009-02-14
Hello! 
I recently took apart my old broken navman iCN 650 gps and found a small 2gb microdrive inside. I tried to use it with the card reader embeded into my desktop box, and the little light even turns on, but I can't see it in ubuntu, even with fdisk. 
It sees regular compact flash cards, but I can't get the microdrive to work.
Is there a way I can fix it or is it just a hardware/power issue?:confused:

Thanks in advance for any help.

---

### Post by cariboo on 2009-02-14
What is the output of:

```
dmesg | tail -n10
```

when you plug your device in? The above command wil print out the last 10 lines on dmesg, the output should look something like this:

```
dmesg | tail -n10
[ 5976.079666] sd 6:0:0:0: [sdc] 1994385 512-byte hardware sectors: (1.02 GB/973 MiB)
[ 5976.083660] sd 6:0:0:0: [sdc] Write Protect is off
[ 5976.083663] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 5976.083665] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 5976.083670]  sdc: **sdc1**
[ 5976.087940] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 5976.088012] sd 6:0:0:0: Attached scsi generic sg3 type 0
[ 5976.107718] sr1: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[ 5976.108016] sr 6:0:0:1: Attached scsi CD-ROM sr1
[ 5976.108097] sr 6:0:0:1: Attached scsi generic sg4 type 5
```

note the device label sdc1 in the above output, you should see something similar if your device is working.

Jim

---

