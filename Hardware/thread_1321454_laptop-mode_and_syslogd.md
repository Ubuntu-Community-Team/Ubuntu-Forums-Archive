---
title: "laptop-mode and syslogd"
date: 2009-11-10
forum: Hardware
---

### Post by philrosenberg on 2009-11-10
Hi
I'm running Jaunty Server on an old Sony VAIO laptop. I'm trying to get the laptop hard drive to spin down when inactive to save a bit of power but mostly because it's quite noisy with it on.
I've set the spin down time to 10 minutes using laptop-mode-tools but it seems that syslogd is stopping the drive spinning down. If I stop syslogd and restart it (#### below is the pid of syslogd):
```

sudo kill ####
sudo /etc/init.d/sysklogd start

```
then spin down occurs as expected. If I reboot the system then again the drive will not spin down. I'm fairly new to linux so any advice on why this might be happening would be much appreciated.
 
Phil

---

