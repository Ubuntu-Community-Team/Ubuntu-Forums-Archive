---
title: "Touchpad won't turn off at startup anymore"
date: 2010-05-04
forum: Hardware
---

### Post by ziekfiguur on 2010-05-04
Hello people,

I have a little script that i use to turn off my touchpad:
```

#!/bin/bash

xinput set-int-prop "AlpsPS/2 ALPS GlidePoint" "Device Enabled" 8 0
echo -e "\033[31mTouchpad is turned off\033[0m"

```

This script is called at startup, (i added it at System > Preferences > Startup Applications) and this all worked fine.
But, since i updated to lucid, for some reason the call at startup doesn't work anymore and the touchpad is still turned on after i have logged in.
However, the weird thing is that when i call the script in a terminal it still works just fine.:confused:

Any ideas about what causes this or how to solve it?

---

### Post by ziekfiguur on 2010-05-07
I did some test with the script: The script is run, and it does work, but apparently the touchpad is turned on again afterwards. 
Does anyone know how i can disable this?

Thanks in advance.

---

