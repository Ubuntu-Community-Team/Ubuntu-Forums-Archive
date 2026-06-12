---
title: "An FYI in mounting RCA mp3 players"
date: 2009-12-12
forum: Hardware
---

### Post by 1oooop on 2009-12-12
I recently mounted an RCA media player by using the second partition on the device rather than the first...

for me this partition is /dev/sdb1 NOT /dev/sdb

so, basically...

```
sudo mkdir /media/mp3player
```

then

```
sudo mount -t /dev/sdb1 /media/mp3player
```

quite a simple solution, really

now leaves the question "what is the first partition then?"
I would assume that the first is a RAW partition containing the firmware of the player... definitely something that you'll wanna mount to mess with :D ; however, I don't think anyone will be able to get the partition going.

---

