---
title: "Executing command on Power Changes"
date: 2011-05-20
forum: Hardware
---

### Post by insecure hyena on 2011-05-20
Hi guys a quick question...how can I run a command (that need root privileges) when I change the energy profile of my laptop (Acer Aspire 4920)? I mean when I plug in to the AC or when I go on battery?
Essentially I need that when I have the AC cable plugged the hd power manager is on, contrariwise, when I'm on battery I need that the hd power manager is off (by executing "sudo hdparm -B 255 /dev/sda").
Thanks to everyone who will help this poor linux novice :oops:

---

### Post by insecure hyena on 2011-06-02
Up!
And I add one more question...I've put a script (00_stop_load_cycle) in /etc/power.d/ and /etc/sleep.d to disable the power management of the hard drive.

```

#!/bin/bash

#Disable hard drive power management
hdparm -B 255 /dev/sda

```

From the log it appears that It is actually called and executed but why when I plug off the AC cable it appears that the power management value is set to 128 instead to 255?!
And the same happens when I come from standby...I really don't get how the power management is done in Ubuntu...
Ah, I'm using the LTS Lucid Lynx.

---

