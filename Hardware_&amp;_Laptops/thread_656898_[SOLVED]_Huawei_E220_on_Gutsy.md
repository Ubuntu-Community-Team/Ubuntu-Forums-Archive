---
title: "[SOLVED] Huawei E220 on Gutsy"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by karl_kashofer on 2008-01-03
Hi !

I had a lot of trouble getting my telering HUAWEI E220 working on Kubuntu Gutsy despite the vast amount of Howtos for it. It seems to me something is different in Kubuntu Gutsy which makes the common udev rules not work.

Here is what works for me:

create a udev rules file /etc/udev/rules.d/50-huawei.rules with the following content:

SUBSYSTEMS=="scsi"  ATTRS{vendor}=="HUAWEI  ", OPTIONS+="ignore_device"

This makes Gutsy ignore the CD device so the modem can work.
Then you can just use kppp according to the other guides to make the connection.

Attention: After creating new or changing udev rules you need to run "sudo udevcontrol reload_rules" or reboot for the changes to take effect.

Hope this helps,
Cheers,
Karl

---

### Post by karl_kashofer on 2008-01-03
Hmmm

Now i added a udev rule like this:

KERNEL=="ttyUSB0", ATTR{dev}=="188:0", SUBSYSTEMS=="usb", ATTRS{product}=="HUAWEI Mobile", ACTION=="add", RUN+="/bin/sh /home/karl/modem.sh", OPTIONS+="last_rule"

to call this:

karl@karl-laptop:~$ cat modem.sh
#! /bin/sh
date +%F_%R >> /home/karl/log.txt
/usr/bin/kdesu -u karl -c "/usr/bin/kppp -c Telering >> /home/karl/log.txt"
karl@karl-laptop:~$

It does the date > log thing, but never starts kppp.
Would anyone know why ?

thanks,
karl

---

