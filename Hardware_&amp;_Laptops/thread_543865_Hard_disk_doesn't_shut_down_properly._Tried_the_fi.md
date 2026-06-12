---
title: "Hard disk doesn't shut down properly. Tried the fix but still...."
date: 2007-09-05
forum: Hardware &amp; Laptops
---

### Post by applegrew on 2007-09-05
I have a laptop and I too also hear the strange pop sounds. I have tried a script to turn-off hard disks properly. Sometimes the pop is soft and sometimes loud and sometimes no sound at all. It is pretty much random. Am I doing the correct thing? The following script
```

#!/bin/sh
echo 1 > /sys/class/scsi_disk/0\:0\:0\:0/stop_on_shutdown
```

has been named S00hdd-shutdown-workaround with executing permission. I have placed this script in /etc/rc0.d. Note I have placed the file itself and not its symbolic link.

---

