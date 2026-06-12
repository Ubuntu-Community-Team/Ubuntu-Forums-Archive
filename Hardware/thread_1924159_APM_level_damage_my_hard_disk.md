---
title: "APM level damage my hard disk"
date: 2012-02-12
forum: Hardware
---

### Post by emanamini on 2012-02-12
Hi there
I have a problem that has reported for ubuntu a long time age
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
I think this problem must have fixed but it doesn't in mint 12 & ubuntu 11.10
after installing smartmontools run this command as root
# smartctl -a /dev/sda | grep Load_Cycle_Count
it showed me 53773 Cycle Count
in 10 minutes I run the same command. the output shock  me. It has been increasing so fast.
After many searches I found that this command would help me and disable APM
# hdparm -B 255 /dev/sda
But When I restart the machine everything goes back.
So I wrote a script like this 

```

#!/bin/sh
hdparm -B 255 /dev/sda

```and named it as disable-APM.sh and placed it under /etc/init.d
Edit /etc/init.d/rc.local and add the following line to the end of it
```

/etc/init.d/disable-APM.sh

```But it was not useful so
I added hdparm -B 255 /dev/sda to the above file but ...
But it didn't affect the system :( and never run the script as root at start up
How can I run this script on system start up as root?
I already run chmod a+x /etc/init.d/disable-APM.sh and it is executable

Edit:
see here
[http://forum.linuxmint.com/viewtopic.php?f=49&t=94336&p=540527]("http://forum.linuxmint.com/viewtopic.php?f=49&t=94336&p=540527#p540527")

---

