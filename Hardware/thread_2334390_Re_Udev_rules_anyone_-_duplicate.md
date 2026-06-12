---
title: "Re: Udev rules anyone? - duplicate"
date: 2016-08-18
forum: Hardware
---

### Post by os2 on 2016-08-18
You know you have to give sudo the appropriate authorisation to the  screen user (ie, sudo) to allow udev to execute the script (as root) on  the executing terminal.

```

#!/bin/bash

export DISPLAY=$(echo $DISPLAY | cut -c -2)
user=$(who | grep :0 | awk '{print $1}' | tail -n1)
export XAUTHORITY=/home/$user/.Xauthority

cmd="sudo DISPLAY=:0.0 -u $user sh"


```

---

