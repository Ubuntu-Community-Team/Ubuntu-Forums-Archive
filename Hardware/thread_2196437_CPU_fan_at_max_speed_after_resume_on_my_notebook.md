---
title: "CPU fan at max speed after resume on my notebook"
date: 2013-12-29
forum: Hardware
---

### Post by franz-knipp on 2013-12-29
After upgrading to Linux Mint 16, based on Ubuntu 13.10, kernel version 3.11.0, I noticed the problem that the fan turned up to maximum speed and didn't go back to normal speeds afterwards.

It looks like kernel bug 58301 ([https://bugzilla.kernel.org/show_bug.cgi?id=58301](https://bugzilla.kernel.org/show_bug.cgi?id=58301)). 

To fix the problem I've created */etc/pm/sleep.d/11_fan_3.11.0*

```
#!/bin/sh
#
# Reset fan speeds after resume, otherwise they blow at maximum speed
#
# Used as work-around for ACPI kernel bug 58301
# https://bugzilla.kernel.org/show_bug.cgi?id=58301
#
# The idea for this fix was taken from 
# http://ubuntuforums.org/showthread.php?t=1761370
#
# Author: franz@qnipp.com
#
# To be saved as /etc/pm/sleep.d/11_fan_3.11.0

case "$1" in
  thaw|resume)
    for i in /sys/class/thermal/cooling_device* ; do 
      type=`cat $i/type`
      if [ "$type" = "Fan" ] ; then 
        echo 0 > $i/cur_state
      fi
  done
  ;;
esac
```

The script turns off all fans, they will be switched on automatically as necessary afterwards.

My notebook is an HP ProBook 4510s, but the fix should help for other models as well.

---

