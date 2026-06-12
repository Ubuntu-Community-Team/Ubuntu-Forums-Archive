---
title: "cdrom polling: how does it affect battery life?"
date: 2009-02-11
forum: Hardware
---

### Post by lavinog on 2009-02-11
First off, I am using a compaq presario notebook v5000 series, with Ubuntu 8.04 (32bit).
A while back, while investigating the excessive HD parking issue, my HD light flashed every 2 secs. I found this to be due to the hald polling the cd drive every 2 secs.
to see if what it is on your system:
```
 pgrep -fl hald-addon-storage

```
mine says:
7717 hald-addon-storage: polling /dev/hdc (every 2 sec)

This constant polling is causing an additional drain on the battery. It may be insignificant, but my battery life is just over 2 hrs which means that my cdrom drive is polled 3600 times. I don't know how much is drawn due to this process, and testing would most likely have a lot of error. The LED should account for 10mAh (based on 20mA and 0.5s on time) which works out to be 0.1% of my total battery capacity (6600mAh). There is also energy used communicating to the drive, and processing the information.

How does windows handle cd drives?
What happens when hald polls the drive?
Why doesn't the drive just tell hald when the drive is ejected and closed?

Also is there a command to change the polling frequency, or if I kill the process how can I restart the process?



I rarely use a cd when on the battery

---

### Post by Yashiro on 2009-02-11
Off:
sudo hal-disable-polling --device /dev/scd0

On:
sudo hal-disable-polling --enable-polling --device /dev/scd0

Drawback:
With polling off the OS can't tell when you insert a CD.
You will have to manually re-scan the drive in nautilus. This only affects popping in a disk for the first time. Works fine after that. Exactly like disabling autoplay in Windows.

---

