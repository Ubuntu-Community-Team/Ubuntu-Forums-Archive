---
title: "Script to control omnibook module"
date: 2010-10-05
forum: Hardware
---

### Post by bulva on 2010-10-05
Hello everybody,

After the installation of [omnibook]("http://sourceforge.net/apps/mediawiki/omnibook/index.php?title=Main_Page") kernel module my laptop (Toshiba Satellite with Insyde H20 BIOS) turns on 5-10 minutes after shutdown. This is a know issue, but I don't know about any existing solution yet.

My idea is to add /etc/init.d/ script loading the module on startup and unloading it on shutdown. Is this script correct:

```
#! /bin/sh
# /etc/init.d/omnibook_module
#

case "$1" in
  start)
  modprobe omnibook ectype=11 battery=1
   ;;
  stop)
  rmmod omnibook
  ;;
    esac
exit 0
```

---

