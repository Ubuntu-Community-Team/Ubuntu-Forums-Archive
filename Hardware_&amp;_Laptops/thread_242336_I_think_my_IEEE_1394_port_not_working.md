---
title: "I think my IEEE 1394 port not working"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by chylee on 2006-08-23
I would like to find out if my IEEE 1394 port is working. I tried to use it for some video editing on the program (Kino) couldn't find it.

---

### Post by chylee on 2006-08-26
I've had no reply to this problem so I hoping someone can help me.

---

### Post by BatteryCell on 2006-10-29
Sorry to bring up a old post. But I had the same problem and for me it was because /dev/1394 didn't exist.  So I wrote a quick little script that fixes this.  Note that sometimes it has to be run twice for some reason...still haven't figured that out, but it still works so...
```

#!/bin/bash
echo "Creating raw1394"
modprobe raw1394
echo "Changing permissions"
sudo chmod a+rw /dev/*1394
echo "The firewire port on the back should now work"
exit 0

```

---

