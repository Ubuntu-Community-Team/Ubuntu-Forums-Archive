---
title: "dmesg error"
date: 2020-01-02
forum: Hardware
---

### Post by cosy2 on 2020-01-02
```
64478.725566] ata1.00: exception Emask 0x50 SAct 0x0 SErr 0x480900 action 0x6 frozen
[64478.725578] ata1.00: irq_stat 0x08000000, interface fatal error
[64478.725586] ata1: SError: { UnrecovData HostInt 10B8B Handshk }
[64478.725594] ata1.00: failed command: WRITE DMA EXT
[64478.725607] ata1.00: cmd 35/00:00:20:4e:46/00:0a:0a:00:00/e0 tag 12 dma 1310720 out
                        res 50/00:80:00:50:28/00:00:00:00:00/ea Emask 0x50 (ATA bus error)
[64478.725618] ata1.00: status: { DRDY }

```

so based off this [https://unix.stackexchange.com/questions/304661/according-to-smart-hard-disk-is-not-broken-but-i-have-errors-in-dmesg](https://unix.stackexchange.com/questions/304661/according-to-smart-hard-disk-is-not-broken-but-i-have-errors-in-dmesg) i got a loss/damaged cable ?

---

### Post by SeijiSensei on 2020-01-02
A bad cable would be the good news. I suspect it could also indicate a problem with the disk itself.

---

### Post by Yellow Pasque on 2020-01-02
Could we see the SMART data on the drive in question?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by cosy2 on 2020-01-02
bad news cable is OK 

ssd is dead while i did try to move files with rsync it did die on me


edit: placing this ssd on other machine works and i can move files

---

### Post by cosy2 on 2020-01-02
> **Yellow Pasque said:**
> Could we see the SMART data on the drive in question?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

sure [https://paste.ubuntu.com/p/kQpjPts345/](https://paste.ubuntu.com/p/kQpjPts345/)

---

