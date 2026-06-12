---
title: "Mount RAID 0 on Ubuntu Start (LDM)"
date: 2017-01-30
forum: Hardware
---

### Post by marceeu on 2017-01-30
Hi guys, It is my first post here. 

I have a Software RAID 0 array assembled In Windows, It Is GPT and LDM, so to mount it in Ubuntu I'm using ldmtool:
```
sudo ldmtool create all
```
It works perfectly, now i need to make this automatic when i boot Ubuntu, i'v tried it editing etc/rc.local like that but **It does not work**:
```
[COLOR=#111111][FONT=Consolas]#!/bin/sh -e[/FONT][/COLOR]#
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
sudo ldmtool create all
exit 0[COLOR=#111111][FONT=Consolas]
[/FONT][/COLOR]
```

How can I solve It?

Thanks

---

### Post by slickymaster on 2017-01-30
*Thread moved to **Hardware**.*

---

### Post by marceeu on 2017-01-30
Any other ways to do it?

---

### Post by ajgreeny on 2017-01-30
You do not need **sudo** at the start of the command used so delete that and try with just **ldmtool create all**.

Commands that are run using /etc/rc.local are run as root automatically; whether using **sudo** stops it from doing what you expect is something I will have to leave to others as my knowledge of raid is just about zero.

---

