---
title: "Custom AC Power/Battery Commands"
date: 2008-05-08
forum: Hardware
---

### Post by frostedegg on 2008-05-08
Ubuntu 8.04
Sony SZ640

The Sony driver does not allow me to adjust the brightness of my LCD.  I am using xbacklight to manually adjust the brightness.  I am wondering if there is a way to add custom user commands to gnome power manager that will run when my laptop switches between AC Power and Battery.

When I go to AC Power, I want to turn the brightness up with a command like: xbacklight -set 85

When I go to Battery, I want to turn the brightness down with a command like: xbacklight -set 25

Anyone know if I can get these commands to run on AC/Battery switches?

Thanks.

---

### Post by sdennie on 2008-05-08
At the moment (it may change in the future), putting scripts in /etc/acpi/ac.d and /etc/acpi/battery.d will do what you want.  Use something like "gksudo gedit" to create the following two files:

In /etc/acpi/ac.d create a file called 99-backlight-high.sh:
```

#!/bin/bash

xbacklight -set 85

```

And in /etc/acpi/battery.d create a file called 99-backlight-low.sh:
```

#!/bin/bash

xbacklight -set 25

```

Then:

```

sudo chmod +x /etc/acpi/ac.d/99-backlight-high.sh
sudo chmod +x /etc/acpi/battery.d/99-backlight-low.sh

```

---

