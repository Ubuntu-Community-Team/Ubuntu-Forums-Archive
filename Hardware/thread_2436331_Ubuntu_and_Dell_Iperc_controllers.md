---
title: "Ubuntu and Dell Iperc controllers"
date: 2020-02-04
forum: Hardware
---

### Post by g3kxyz on 2020-02-04
I'm sorry if this has been asked before but I'm hoping to figure out a way to view SMART data on a Ubuntu server that has Raid 5 using Dell Iperc controllers. 

I tried the normal smarttools and so far haven't had great success.

The data I'm after is to view potential drive failures or future failures on servers like this.

---

### Post by SeijiSensei on 2020-02-04
You can't see the individual drives from Linux, because the PERC controller presents the array as a single device to the operating system.

It might be possible at boot using the controller's firmware:  [https://www.dell.com/community/PowerEdge-HDD-SCSI-RAID/read-disk-S-M-A-R-T-in-PERC-H710-Mini/td-p/4495826](https://www.dell.com/community/PowerEdge-HDD-SCSI-RAID/read-disk-S-M-A-R-T-in-PERC-H710-Mini/td-p/4495826)

---

### Post by g3kxyz on 2020-02-04
> **SeijiSensei said:**
> You can't see the individual drives from Linux, because the PERC controller presents the array as a single device to the operating system.

It might be possible at boot using the controller's firmware:  [https://www.dell.com/community/PowerEdge-HDD-SCSI-RAID/read-disk-S-M-A-R-T-in-PERC-H710-Mini/td-p/4495826](https://www.dell.com/community/PowerEdge-HDD-SCSI-RAID/read-disk-S-M-A-R-T-in-PERC-H710-Mini/td-p/4495826)

I was afraid that it might only be possible at boot. When these Dell servers are running windows you can install "Server Administrator" which lets you see the disks but they don't seem to have one that works with linux.

---

