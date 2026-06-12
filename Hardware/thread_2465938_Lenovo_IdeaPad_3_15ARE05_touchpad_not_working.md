---
title: "Lenovo IdeaPad 3 15ARE05 touchpad not working"
date: 2021-08-15
forum: Hardware
---

### Post by marsdenf on 2021-08-15
I just got a new IdeaPad 3 15ARE05 81W4  laptop and immediately installed Xubuntu 20.04 on it.  Everything works except the touchpad.  The touchpad is not even recognized by the OS.  Tried a live usb of Xubuntu 21.04, but the touchpad didn't work with that either.  Anyone have a fix for this?

---

### Post by marsdenf on 2021-08-25
I tried the fix described here:  [https://askubuntu.com/questions/1248176/ideapad-5-15are05-elan-touchpad-not-working-on-20-04-nor-on-18-04/1250962#1250962](https://askubuntu.com/questions/1248176/ideapad-5-15are05-elan-touchpad-not-working-on-20-04-nor-on-18-04/1250962#1250962).
  
 Namely: 
  
 
8
 It seems not to be possible to blacklist elants_i2c driver, as it is a built-in kernel module for Ubuntu:
 stefano@stefano-IdeaPad-5-15ARE05:~$ modinfo elants-i2c
name:           elants_i2c
filename:       (builtin)
license:        GPL
description:    Elan I2c Touchscreen driver
author:         Scott Liu <scott.liu@emc.com.tw>
 so there is a faster way than compiling the kernel. Just create a SystemD unit like the below:
 stefano@stefano-IdeaPad-5-15ARE05:~$ cat /etc/systemd/system/touchpadfix.service 
[Unit]
Description=Fix touchpad issue by binding correct driver
 [Service]
ExecStart=/usr/local/bin/touchpadfix
Type=oneshot
RemainAfterExit=yes
 [Install]
WantedBy=multi-user.target
 and create /usr/local/bin/touchpadfix file as follows
 stefano@stefano-IdeaPad-5-15ARE05:~$ cat  /usr/local/bin/touchpadfix
#!/bin/bash
modprobe i2c_hid
echo "i2c-ELAN0001:00" > /sys/bus/i2c/drivers/elants_i2c/unbind
echo "i2c-ELAN0001:00" > /sys/bus/i2c/drivers/i2c_hid/bind
 and then make it executable, enable and start the unit with the following commands:
 chmod +x /usr/local/bin/touchpadfix
sudo systemctl daemon-reload
sudo systemctl enable --now touchpadfix.service
 and touchpad should start to work immediately!



  
 Now the touchpad works, except for the right-click,  which acts as a  single left click.   Also noticed that if the touchpad is changed to  left-handed,  then single clicking anywhere on the pad acts as a  right-click.
  
 Anyone know how to fix the right click on this IdeaPad?


NEW UPDATE:  It turns out I wasn't using the touchpad correctly.   Right click is by single click on the bottom right corner, or two finger click anywhere.  Will now mark this as solved.

---

