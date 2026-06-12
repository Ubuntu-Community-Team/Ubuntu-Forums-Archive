---
title: "How to run a root command at login?"
date: 2008-05-07
forum: Hardware
---

### Post by Vadi on 2008-05-07
I need to run "sudo hdparm -B 255 /dev/sda1" to prevent whatever power management gets enabled from parking my drive head every 2.5 seconds and driving me crazy. Does anyone know how to get around the password problem though?

---

### Post by kerry_s on 2008-05-07
drop the sudo and put the rest of your line in /etc/rc.local that's run as root. don't forget to put & at the end so it doesn't stop on errors.

---

### Post by sdennie on 2008-05-07
Rather than doing that, have you tried editing /etc/hdparm.conf (or just putting the hdparm command /etc/rc.local)?  The settings there should be executed at boot time however, they will not persist across a suspend/resume.  In Hardy, if you want the settings to persist create an executable script called /usr/lib/pm-utils/sleep.d/99-disk with the hdparm call (a bit of a hack but, it works).

---

### Post by Vadi on 2008-05-07
So "sudo nano /usr/lib/pm-utils/sleep.d/99-disk", paste "hdparm -B 255 /dev/sda1", save, exit, and I'm good?

---

### Post by sdennie on 2008-05-07
I would save it as:

```

#!/bin/bash

hdparm -B 255 /dev/sda1

```

And then do a:

```

sudo chmod +x /usr/lib/pm-utils/sleep.d/99-disk

```

Note: Along with this method, you'll still have to use one of the other methods above to get the hdparm setting to work at boot time.

---

### Post by Vadi on 2008-05-08
I uncommented the line in the .conf to be like this now:

> # -q be quiet
quiet
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management



Would that work?

---

### Post by sdennie on 2008-05-08
I'm not sure but, I don't think so.  If you go to the bottom of hdparm.conf and just uncomment the 3 lines that start with "command_line" and edit the hdparm command to be "hdparm -B 255 /dev/sda", I think that will work right.

---

### Post by Vadi on 2008-05-08
Thanks, I'll give that a try.

---

