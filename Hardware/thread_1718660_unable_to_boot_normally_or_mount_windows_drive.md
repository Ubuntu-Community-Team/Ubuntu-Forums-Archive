---
title: "unable to boot normally or mount windows drive"
date: 2011-03-31
forum: Hardware
---

### Post by the_jlx on 2011-03-31
so everything was working fine again after i reinstalled ubuntu.
( [http://ubuntuforums.org/showthread.php?t=1712104&highlight=Error+reading+bootsector%3A+Input%2Foutput+error]("http://ubuntuforums.org/showthread.php?t=1712104&highlight=Error+reading+bootsector%3A+Input%2Foutput+error") )
Then i updated and i am back to having problems.
at boot= 
```
ata5.00 failed command: SET FEATURES
ata5.00 cmd ef/05:fe:00:00:00/00:00:00:00:00/40 tag 0
res 40/00:00:00:00:00/00:00:00:00:00/40 emask 0X4 (timeout)

ata5.00: status { DRDY }
sd 4:0:0:0:0: timing out command, waited 7 s
```

when inside system=

```
Error mounting: mount exited with exit code 13: Error reading bootsector: Input/output error
Failed to sync device /dev/sdb1: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

---

### Post by the_jlx on 2011-03-31
bump...

---

### Post by the_jlx on 2011-04-03
...Sigh

---

### Post by the_jlx on 2011-04-04
solved it by accident i installed ubuntu 11.04 beta trough windows...
sits confused but happy

---

