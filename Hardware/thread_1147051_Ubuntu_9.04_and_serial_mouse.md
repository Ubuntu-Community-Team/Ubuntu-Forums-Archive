---
title: "Ubuntu 9.04 and serial mouse"
date: 2009-05-03
forum: Hardware
---

### Post by Michal1983 on 2009-05-03
In version 8.10 when i paste
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/ttyS0"
    Option         "Protocol" "Microsoft"
    Option         "ZAxisMapping" "4 5"
EndSection
``` to the /etc/X11/xorg.conf my simply two button mouse which is connected to COM1 was working. After actualization 8.10 to 9.04 mouse stop working. I do the same things but nothing work. After some posts on one of forum i discover that comand
```
sudo inputattach -bare /dev/ttyS0
``` makes that my mouse is working again. But is tiring write this command after every system run. Is there any solution which helps me use this mouse again automatic without inputing any commands?

---

### Post by rameshg87 on 2009-07-01
Thanks friend. Atleast there is one solution. Looks like we are the only one using the serial mouse these days.. How about putting it in a script and adding it gnome startup ?

---

### Post by ivgelder on 2009-10-09
Thanks, finally i found a solution for my problem

---

### Post by ivgelder on 2009-10-09
after some trying, i figured out

```

Section "InputDevice"
Identifier "Configured Mouse"
Driver "Mouse"
Option "CorePointer"
Option "Device" "/dev/ttyS0"
Option "Protocol" "Microsoft"

```worked for me

---

