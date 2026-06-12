---
title: "Hard-drive problems"
date: 2009-01-10
forum: Hardware
---

### Post by shade11 on 2009-01-10
Whenever I boot up into Ubuntu I get a series of errors relating to an 80GB SATA hard-drive in my computer. Even after building myself a new computer (keeping the same hard-drives) the error continues. I have received this error in both a Live CD and when installed. Normally, when booting off a live CD, these errors go on and I eventually boot into X. When I boot off my harddrive I get the same series of errors though it hangs after a certain part.

```
ata.01 status {DRDY ERR}
ata.01 error {UNC}
end_request: I/O error, dev sdb, sector 56
Buffer I/O error on device sdb, logical block 7
```

Normally I type in exit and it continues. But these errors increase my boot time and it requires my input in order to continue booting properly.

Is there a way to stop these errors?

---

### Post by cariboo on 2009-01-10
I would suggest booting from the LiveCD and running fsck on the drive to clear up the errors. Make sure that the drive isn't mounted, then in a terminal type:

```
fsck /dev/<sata_drive>
```

Where <sata_drive> is the device label.

Jim

---

