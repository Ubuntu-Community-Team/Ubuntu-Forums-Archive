---
title: "Power Down Sata Drives"
date: 2008-09-10
forum: General Help
---

### Post by rampageoberon on 2008-09-10
Hi,

I wanted to configure my system to power down my drives (All SATA in SCSI mode).

I have read that hdparm can not be used to spin down sata drives. Could someone please point out where to look for more info or how I can go about spinning my drives down after a period of no activity?

Thanks

---

### Post by iaculallad on 2008-09-10
What about using sdparm?

```
sudo apt-get install sdparm
```

Trying to 'turn-off' at 3 minute timeout:

```
sudo sdparm --set SCT=30 /dev/sdb
```

Try reading the manual:

```
man sdparm
```

---

### Post by rampageoberon on 2008-09-10
Thanks very much for that. Will test it and check.

---

### Post by rampageoberon on 2008-09-10
I get the following error on trying this. Any ideas what might be causing this and how to fix it?

```

~ bash$ sudo sdparm --set=SCT=18000 /dev/sdb
    /dev/sdb: ATA       SAMSUNG HD103UJ   1AA0
change_mode_page: failed fetching page: Power condition
```

---

### Post by rampageoberon on 2008-09-10
Any ideas how to fix the issue where power condition page is not found? I gather its a software issue rather than hardware

```
~ bash$ sudo sdparm -a -l --page=poo /dev/sda
    /dev/sda: ATA       ST3500630AS       3.AA
    Direct access device specific parameters: WP=0  DPOFUA=0
>> Power condition - old version [poo] mode page not found

```

Thanks again

---

### Post by sdennie on 2008-09-10
Actually, hdparm should work just fine on SATA drives.  Try using:

```

sudo hdparm -I /dev/sda

```

As for spinning down the drives, that's very hard to do because the system tends to write to disk a lot.  Unless you are willing to take extreme measures, getting the disks to completely spin down is not really possible (at least not for long periods of time).  You can however decrease disk activity: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998")

---

