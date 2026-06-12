---
title: "Ubuntu Server 64 bit on a Raspberry Pi 4 RTC real time clock HELP"
date: 2022-02-21
forum: Hardware
---

### Post by darknewt on 2022-02-21
Hi All,

I have successfully managed to install an RTC DS3231 on raspbian, however I can't get it working on ubuntu. 

I have installed the I2c tools and it's detected on 0x68, after that the guides etc.. are either totally out of date or incomplete.   If anyone has managed this I would be grateful for a step by step on how you did it, if you know how I am more than happy to help you write a guide for it and be your guinea pig!!

Cheers!!

---

### Post by #&amp;thj^% on 2022-02-21
Have you yet created a SystemD unit file.
EG:
My unit file looks like this:
```

[Unit]
Description=Enable DS3231 I2C RTC

[Service]
Type=oneshot
ExecStartPre=/bin/bash -c "echo ds1307 0x68 | tee /sys/class/i2c-adapter/i2c-1/new_device"
ExecStart=/sbin/hwclock -s

[Install]
WantedBy=basic.target
```

The ExecStartPre pokes some magic values7 into the right place in the right places in sysfs to get the I2C bus to detect the device, and the ExecStart runs hwclock to set the system time. I&#8217;m setting this unit to be WantedBy basic.target, so the clock gets set correctly as early in the boot process as possible.
EDIT: To enable the unit, write the file to **"/etc/systemd/system/ds3231.system"**, and run **"systemctl enable ds3231"** to set it to run on boot.
Also this may provide how to add a unit: [https://www.tecmint.com/create-new-service-units-in-systemd/](https://www.tecmint.com/create-new-service-units-in-systemd/)
If more is needed just ask.

---

