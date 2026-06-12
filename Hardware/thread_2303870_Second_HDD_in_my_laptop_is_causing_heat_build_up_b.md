---
title: "Second HDD in my laptop is causing heat build up but it's not mounted."
date: 2015-11-22
forum: Hardware
---

### Post by J_Me on 2015-11-22
Currently running kubuntu 1404. As the title says the disc isn't even mounted but makes more noise than the fan. I thought there was something under settings > power management for controlling hard disc drives but maybe it's been removed. Or should I look into how to use hdparm.[br]1[/br]  Thanks

---

### Post by efflandt on 2015-11-22
The command for setting power saving settings for a drive is **hdparm**. It has to be run as root, so if you do it somewhere other than a startup script like /etc/rc.local (like to test it from the shell) you would need to use "sudo " prefix. See "man hdparm". "-S 1" (capital S) option would set the drive to sleep in 5 seconds. "-y" (small y) would put the drive to sleep immediately, but it would not automatically go back to sleep if you wake it up.

---

### Post by J_Me on 2015-11-23
Thank you very much

---

