---
title: "DVD not working in Ubuntu 9.04,Unable to mount  message"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by sameerlatheef on 2009-08-23
I am a new user of Ubuntu 9.04.I am using compaq Presario cq 40.My dvd is not working in  Ubuntu,tried the commands seen in forum and the results are as shown ,pls guide me


 
 sudo mount -t iso9660 /dev/scd0 /media/cdrom0
[sudo] password for sameer: 
mount: no medium found on /dev/sr0

$ dmesg | tail -n10
[ 4441.768587] sd 6:0:0:0: [sdb] Write Protect is off
[ 4441.768595] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4441.768599] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4441.774185] sd 6:0:0:0: [sdb] 2001888 512-byte hardware sectors: (1.02 GB/977 MiB)
[ 4441.774870] sd 6:0:0:0: [sdb] Write Protect is off
[ 4441.774877] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 4441.774882] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 4441.774891]  sdb: sdb1
[ 4441.779202] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 4441.779331] sd 6:0:0:0: Attached scsi generic sg2 type 0

---

