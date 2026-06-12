---
title: "Help me with this script (hdparm)"
date: 2008-11-05
forum: General Help
---

### Post by bladerunner6 on 2008-11-05
I want to run a shell script so that hdparm always sets my hard drives either in quiet mode or loud mode,

in windows this is what i have in a normal .bat file
hdparm -M 254 /dev/hda

hdparm -M 254 /dev/hdb


in linux how should i display this ?
#!/bin/bash

HDPARM='/sbin/hdparm -M 254 /dev/sda '
HDPARM='/sbin/hdparm -M 254 /dev/sdb '
exit 0

anyone help in rectifying the above

---

### Post by jpkotta on 2008-11-06
All you did was define a variable that held the command you wanted.

```

#!/bin/sh

HDP=/sbin/hdparm

for dev in /dev/hda /dev/hdb ; do
    $HDP -M 254 $dev
done

exit 0

```

---

### Post by bladerunner6 on 2008-11-10
thanks for that,

---

### Post by spibou on 2008-11-10
> **jpkotta said:**
> All you did was define a variable that held the command you wanted.

```

#!/bin/sh

HDP=/sbin/hdparm

for dev in /dev/hda /dev/hdb ; do
    $HDP -M 254 $dev
done

exit 0

```
It's better if the script doesn't have exit 0 at the end. This way if something goes wrong with hdparm the exit value of the script will reflect that but if it has exit 0 at the end it will look as if it always terminated succesfully.

---

### Post by bladerunner6 on 2008-12-01
final question,
how do enable normal users to run this scripts?

hdparm needs sudo

---

