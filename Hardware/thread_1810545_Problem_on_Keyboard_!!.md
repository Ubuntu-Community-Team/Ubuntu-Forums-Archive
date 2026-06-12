---
title: "Problem on Keyboard !!"
date: 2011-07-23
forum: Hardware
---

### Post by sady92 on 2011-07-23
Hi,

Well my problem is when i close my laptop (suspend, lock, suspend) when i open it my keyboard dose not work at all..

My Laptop model is a Sony Vaio VGN-CS11Z...

What can be the problem ?

Thankyou.

---

### Post by Toz on 2011-07-23
Try this: Create an executable file called **/etc/pm/sleep.d/70-keyboard_reset** with the following contents:
```
#!/bin/sh
# Reload keyboard interface for sleep/resume

case $1 in
  hibernate|suspend)
    echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
    ;;
  thaw|resume)
    echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind
    ;;
  *)
    ;;
esac
```

_HowTo:_
1. To create the file (from a terminal window):
```
gksduo gedit /etc/pm/sleep.d/70-keyboard_reset
```
2. Copy/paste the above and save the file.
3. Back at the terminal window, type:
```
sudo chmod +x /etc/pm/sleep.d/70-keyboard_reset
```
4. Try sleep/resume.

If it doesn't work, run the following commands in the terminal window and post back the results:
```
lsmod
dmesg
```
as well as posting back the contents of **/var/log/pm-suspend.log**

---

