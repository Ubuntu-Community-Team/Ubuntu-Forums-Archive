---
title: "USB stick cannot be mounted."
date: 2008-11-06
forum: Hardware
---

### Post by Ewan the moomintroll on 2008-11-06
Since updating to 8.10 when I plug in my bytestor usb flash drive I get the following error:
[IMG]http://img243.imageshack.us/img243/5944/screenshotzo3.png[/IMG]
Very annoying.

Thanks for any help you can give.

Edit: thanks constrictor, but no luck.

---

### Post by constrictor on 2008-11-06
you might want to check your /etc/fstab file. I had an issue when i unstalled intrepid from USB there was an entry for USB. I removed it and the issue was solved. Remember only the USB entry. Removing anything else might give you errors mounting other drives. So be careful with this one.

---

### Post by Ewan the moomintroll on 2008-11-07
I'm getting this with all USB devices I think. At least my USB stick and camera.

---

### Post by taurus on 2008-11-07
After plug in your USB thumbdrive, open a terminal and post the output of this command here.

```
dmesg | tail
```

---

### Post by Ewan the moomintroll on 2008-11-07
[  640.417119] sd 2:0:0:0: [sdb] Write Protect is off
[  640.417131] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  640.417135] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  640.420983] sd 2:0:0:0: [sdb] 4030464 512-byte hardware sectors (2064 MB)
[  640.422420] sd 2:0:0:0: [sdb] Write Protect is off
[  640.422430] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  640.422435] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  640.423116]  sdb: sdb1
[  640.427651] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  640.429165] sd 2:0:0:0: Attached scsi generic sg2 type 0

---

### Post by Ewan the moomintroll on 2008-11-10
If i use Gnomad2 with my mp3 player it works perfectly.

FIXED! got a hal update today and it works. I'm as happy as a beaver.

---

### Post by Lifes_Reject on 2008-12-26
> **Ewan the moomintroll said:**
> If i use Gnomad2 with my mp3 player it works perfectly.

FIXED! got a hal update today and it works. I'm as happy as a beaver.
I'm glad you did, I've not got a Hal update and mine don't work after bootup except for maybe 30 seconds. ](*,)

---

