---
title: "UServer boot - Will not automount USB disks"
date: 2009-06-12
forum: Hardware
---

### Post by thhv on 2009-06-12
Hi,
 
Just converted my Squeezecenter music server to ubuntu 9.04 server for performance reasons. (Compaq laptop 1 GHz, 768Mb).
 
My music files are located on a 50% partitionsplitted WD 1 Tb USB disk. It's attached to a USB 2.0 PCMCIA card with two USB ports. I also have a 200 Gb USB disk witch is later ment for backup attached to the other USB port. I Used Webmin to create the mount points.
 
Both USB disks are not mounted at boot. I guess the USB disk are not initalized before system go through fstab? Where should i look for errors?
(Tried 8.04LTS and mount by UUID and LABEL)

---

### Post by thhv on 2009-06-13
I have made a workaround. I guess you can make this pure Linux but I like the Webmin package as a console.
 
1. In Webmin - System - Bootup and Shutdown. 
2. Edit mountall.sh and put in a line at the top of the script "sleep 1" like this:
```
 
#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountall
# Required-Start:    checkfs
# Required-Stop: 
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount all filesystems.
# Description:
### END INIT INFO
sleep 1        [COLOR=red]#<------ put in this line[/COLOR]
PATH=/sbin:/bin
. /lib/init/vars.sh
 
......

```
3. Save and activate mountall.sh at boot.
 
Maybe some other systems need a longer thinking time then 1 sec...
 
I consider this as a workaround – not a solution. I think the Ubuntu team has to make the appropriate changes to the kernel so it’s initializing the disks before it uses them.

---

