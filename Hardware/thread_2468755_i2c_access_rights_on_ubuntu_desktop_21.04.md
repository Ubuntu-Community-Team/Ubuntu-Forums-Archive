---
title: "i2c access rights on ubuntu desktop 21.04"
date: 2021-11-09
forum: Hardware
---

### Post by anthony64480 on 2021-11-09
I am trying to keep access to the i2c interface as a non-root user even when I reboot the Raspberry with Ubuntu Desktop 21.04, as by running these commands on the current system session they are retained:
```

sudo groupadd i2c sudo
chown :i2c /dev/i2c-1 sudo
chmod g+rw /dev/i2c-1
sudo usermod -aG i2c pi

```
To preserve access to the non-root user pi, I added a rule on /etc/udev/rules.d/10-local_i2c_group.rules
```

KERNEL=="i2c-[0-9]*", GROUP="i2c"

```
but if on next reboot, I launch the command
```

i2cdetect -y 1

```
it returns me the following error message:
> Error: Could not open file `/dev/i2c-1': Permission denied
How can I solve? Thanks

---

