---
title: "External Hardrive not Mounting"
date: 2008-09-21
forum: Hardware
---

### Post by Satanis on 2008-09-21
I have a Gateway computer with Ubuntu installed. I also have a Western Digital External Hard Drive. (160GB) I can't get it to mount properly. Any ideas? (Hope I posted this in the right area...probably didn't so oh well.)

---

### Post by cariboo on 2008-09-21
Plug your hard drive in, then in a terminal type:

```
dmesg
```

This should output something like this:

```
[41820.047558] sd 6:0:0:0: [sdc] 1981440 512-byte hardware sectors (1014 MB)
[41820.049049] sd 6:0:0:0: [sdc] Write Protect is off
[41820.049052] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[41820.049054] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[41820.051731] sd 6:0:0:0: [sdc] 1981440 512-byte hardware sectors (1014 MB)
[41820.053177] sd 6:0:0:0: [sdc] Write Protect is off
[41820.053183] sd 6:0:0:0: [sdc] Mode Sense: 43 00 00 00
[41820.053185] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[41820.053190]  sdc: sdc1
```

Notice on the last line, the device I plugged in is sdc1, so if I wanted to mount the device manually in a terminal I would type this:

```
sudo mount /dev/sdc1 /mnt
```

Jim

---

### Post by Satanis on 2008-09-22
YAY!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! IT WORKS!!!!!!!!!!!!!!!!!

Thank you very much. You are the first person that's ever been able to get my external hard drive mounted :D

---

