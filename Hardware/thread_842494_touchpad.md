---
title: "touchpad"
date: 2008-06-27
forum: Hardware
---

### Post by cygnis1 on 2008-06-27
I am running Ubuntu Hardy on my laptop and am looking for a mouse/touchpad controller.  In gutsy I had kde installed and was able to use something called kcontroller ( I think).  I could turn off the touchpad and had to turn it off everytime I restarted the laptop.  I liked that.  Now using mouse prefferences in hardy I can turn off the touchpad but it is "permanent".  I would like one that would work only during the current session.  I use a wireless mouse at home, but don't always take it with me when I travel.  I am afraid that I will go somewhere without the mouse and not be able to use the computer.  Is there a controller I can get would be session specific?
Thanks,
Cygnis1

---

### Post by MarcoL on 2008-06-28
You can use synclient as described in [this page]("https://help.ubuntu.com/community/SynapticsTouchpad#Configuration%20with%20synclient").
Its effect is limited to the current session.

This script is based on synclient, and simply turns on/off the touchpad.
Here is the code:

```
#!/bin/bash

# Touchpad Switch
# It requires SHMConfig enabled as described in https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig

TpadStatus=`synclient -l | awk '/TouchpadOff/ { print $3 }'` #0 means On, 1 means Off
if [ "$TpadStatus" -eq "0" ] 
then
  synclient TouchpadOff=1
  echo "Touchpad now disabled"
else 
  synclient TouchpadOff=0
  echo "Touchpad now enabled"
fi
```

You have save it in a file, and can execute it from a terminal or create a launcher.

---

