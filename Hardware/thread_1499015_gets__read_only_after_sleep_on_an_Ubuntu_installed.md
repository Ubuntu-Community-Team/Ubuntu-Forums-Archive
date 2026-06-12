---
title: "/ gets  read only after sleep on an Ubuntu installed on a SD card"
date: 2010-06-01
forum: Hardware
---

### Post by hanoc on 2010-06-01
Hi,
I've installed UNR 10.04 on a asus eeepc T101MT as explained [here]("http://ubuntuforums.org/showthread.php?t=1497151").

Right now whem my system rstores from sleep / gets read only. I can only solve it by rebooting (at least I know no better).

I guess it has something to do with /etc/fstab.

Right now it's contents are:
```
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=46fcfdb5-ead8-4cdc-971c-e9558ade2ac3 /               ext4    noatime 0       1
tmpfs /tmp tmpfs defaults 0 0
tmpfs /var/tmp tmpfs defaults 0 0
tmpfs /var/log tmpfs defaults 0 0
```
Originally the / line was
```
UUID=46fcfdb5-ead8-4cdc-971c-e9558ade2ac3 /               ext4    noatime,errors=remount-ro 0       1
```
but it made no difference.

I haven't find a errors=remount-rw or similar but I guess the solution should be not to get errors, in case this is what is happening and I'm not sure of that.

Does anyone succeed in restoring an SD installed system from sleep?

Anny suggestion would be greatly appreciated.

Thanks!

---

