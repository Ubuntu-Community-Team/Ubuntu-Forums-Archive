---
title: "suspend and hibernate failures"
date: 2009-07-13
forum: Hardware
---

### Post by xerces8 on 2009-07-13
I have Ubuntu 9.04 (up to date) on my PC (installed it week or two ago) and neither suspend or hibernate work.

I discovered the removing the zd1211rw module helps, but not much.

Details:


With default settings:


suspend:  monitor goes off, computer stays on, does not come back, can only reboot with MagicSysRq+B


hibernate: screen goes dark, then to text mode, then is stays like that, I can switch VTs, but nothing seems to work, except reboot with MagicSysRq+B


with added file /etc/pm/sleep.d/49-rmmod-wifi.sh (see below for contents) :

suspend: works, but resume takes 30 seconds

hibernate: does not work, starts, then after a few seconds the unlock dialog appears (password...)

/etc/pm/sleep.d/49-rmmod-wifi.sh contents:
```
#!/bin/sh
#
# remove wireless module

case "$1" in
        hibernate|suspend)
                modprobe -r zd1211rw
                ;;
        thaw|resume)
                modprobe zd1211rw
                ;;
esac

```

Should I remove more modules ? (if that helps, why aren't simply all of them removed by default ? ;) )

Please point me to some direction to resolve this.

---

### Post by xerces8 on 2009-07-13
Here is the output of lshw.

---

### Post by deadd on 2009-07-14
try looking at this site, even if you don't have a Toshiba Laptop:

[http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html](http://swinky-linuxblog.blogspot.com/2009/05/ubuntu-904-on-toshiba-satellite-l305.html)

If you look at step one, then look at a comment down below, a user couldn't get suspend to work, and afterwards he can.

Hope that this helps.

---

### Post by xerces8 on 2009-07-14
it does not help :(

---

