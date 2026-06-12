---
title: "How to go to standby from Terminal?"
date: 2010-03-01
forum: Hardware
---

### Post by mpw on 2010-03-01
Hello,

I'm using Ubuntu 9.10 on my laptop (MD 95500). Standby works fine for me - activated from the gui.

But I can't activate standby from the terminal.

When I run
```
sudo /etc/acpi/sleep.sh
```
nothing happens.


As Standby works really perfect for me, it can't be so tricky to find the right command for that.

Which command uses the gnome-gui? For exmaple when I close my notebook, it goes to standby....

I searched around a while, just couldn't find anything.

Thanks for help

Bye
MPW

---

### Post by tgalati4 on 2010-03-01
Here's a thread on laptop lid closing events.  Perhaps you could run a script that simulates closing the lid:

[http://ubuntuforums.org/showthread.php?t=1076486&highlight=echo+laptop+lid+sleep](http://ubuntuforums.org/showthread.php?t=1076486&highlight=echo+laptop+lid+sleep)

There are several ways to put your machine to sleep.  The active methods are described in:

cat /etc/default/acpi-support

man pm-suspend

---

### Post by mpw on 2010-03-02
Hello,

thanks for your answer.

Gonna try pm-suspend...

Bye
MPW

---

### Post by mpw on 2010-03-05
Hello again,

okay, pm-suspend works great.

Just one last point: When reawaking the laptop from standby, it doesn't ask for my password.

When I go to standby by closing the laptop, it asks for the password...

Any idea?

Thanks so far

Bye
MPW

---

### Post by jongkind on 2010-03-05
> **mpw said:**
> Hello again,

okay, pm-suspend works great.

Just one last point: When reawaking the laptop from standby, it doesn't ask for my password.

When I go to standby by closing the laptop, it asks for the password...

Any idea?

Thanks so far

Bye
MPW

The following script works fine for me:

#! /bin/bash
gnome-screensaver-command --lock
sleep 5
dbus-send --system --print-reply --dest=org.freedesktop.Hal \
/org/freedesktop/Hal/devices/computer \
org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0

grtz, Herman

---

