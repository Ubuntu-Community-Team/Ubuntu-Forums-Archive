---
title: "Surface Pro 3 - avoiding INT33C2 interrupt spam without losing touchscreen support?"
date: 2021-06-03
forum: Hardware
---

### Post by mewingatthemoon on 2021-06-03
I recently got a used Surface Pro 3, and wound up putting Xubuntu on it. Problem: the whole desktop lags by default, and battery life is 30% shorter than it should be, because the ambient light sensor (INT33C2:00) spams interrupts.

I was able to avoid this by blacklisting the i2c_hid module that handles the light sensor. However, this disables the Surface's touchscreen, which also relies on i2c_hid.

The light sensor has a directory in /sys... several actually, all symlinking to this one:

```

% ls /sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/INT33C2:00 -l
total 0
-r--r--r-- 1 root root 4096 Jun  3 18:56 adr
-r--r--r-- 1 root root 4096 Jun  3 18:56 hid
-r--r--r-- 1 root root 4096 Jun  3 18:56 hrv
drwxr-xr-x 3 root root    0 Jun  3 17:26 INT33C9:00
drwxr-xr-x 3 root root    0 Jun  3 17:26 INT33CA:00
drwxr-xr-x 3 root root    0 Jun  3 17:26 INT33CB:00
drwxr-xr-x 3 root root    0 Jun  3 17:26 INT33D1:00
drwxr-xr-x 3 root root    0 Jun  3 17:26 INT33D7:00
-r--r--r-- 1 root root 4096 Jun  3 17:26 modalias
drwxr-xr-x 3 root root    0 Jun  3 17:26 MSFT1111:00
drwxr-xr-x 3 root root    0 Jun  3 17:26 MSHW0030:00
-r--r--r-- 1 root root 4096 Jun  3 18:56 path
lrwxrwxrwx 1 root root    0 Jun  3 17:26 physical_node -> ../../../../pci0000:00/INT33C2:00
lrwxrwxrwx 1 root root    0 Jun  3 17:26 physical_node1 -> ../../../../pci0000:00/INT33C2:00/i2c-0
drwxr-xr-x 2 root root    0 Jun  3 17:26 power
-r--r--r-- 1 root root 4096 Jun  3 18:56 power_state
-r--r--r-- 1 root root 4096 Jun  3 18:56 status
lrwxrwxrwx 1 root root    0 Jun  3 17:26 subsystem -> ../../../../../bus/acpi
-rw-r--r-- 1 root root 4096 Jun  3 18:03 uevent
-r--r--r-- 1 root root 4096 Jun  3 18:56 uid

```

I used to do some IT work with Linux servers, but I have to admit this is pretty inscrutable to me. If I wanted to completely disable the light sensor so that it stopped spamming interrupts, how would I do that?

Failing that, if there's no way but to keep i2c_hid disabled - is there a way to make the touchscreen use libinput or some other driver instead?

---

### Post by tea for one on 2021-06-04
I can't help you directly with this problem but here is some further information about Surface devices:-

[https://github.com/linux-surface/linux-surface/wiki/Supported-Devices-and-Features](https://github.com/linux-surface/linux-surface/wiki/Supported-Devices-and-Features)

This link was mentioned in the Ubuntu Podcast [https://ubuntupodcast.org/](https://ubuntupodcast.org/)

---

### Post by mewingatthemoon on 2021-06-04
Thanks! Unfortunately that site isn't very helpful - in fact, the page for the SP3 is empty. :(

---

### Post by tea for one on 2021-06-04
Did you see the info about a patched kernel?

[https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup](https://github.com/linux-surface/linux-surface/wiki/Installation-and-Setup)

---

### Post by dddman on 2021-06-04
If you do not find an answer here there is the linux-surface/community.

[https://gitter.im/linux-surface/community](https://gitter.im/linux-surface/community)

---

### Post by mewingatthemoon on 2021-06-04
@tea for one

Thanks, I missed that! Or rather didn't realize it did actually support Secure Boot. I'll give it a try.

@dddman

Thanks, I'll check that out too.

Edit: @tea, the linux-surface kernel actually makes the situation even worse :| i2c_hid related interrupts go from consuming maybe 4-5 watts to more like 16. I'm beginning to think this is a hardware issue, and the ambient light sensor is spamming interrupts because it's damaged.

Edit 2: the actual problem seems to be i2c_designware, not i2c_hid; the former depends on the latter, but is built into Ubuntu kernels rather than as a module. Fortunately it can be disabled as detailed here:

[https://unix.stackexchange.com/questions/423797/how-do-i-disable-i2c-designware-support-when-its-not-built-as-a-module](https://unix.stackexchange.com/questions/423797/how-do-i-disable-i2c-designware-support-when-its-not-built-as-a-module)

Unfortunately this still seems to disable the touchscreen. The search continues. :( But I'm going to note that there are *numerous* stories floating around of weird buggy behavior caused by the i2c_designware driver. It may just not be a very good quality driver I guess.

Edit 3: yeah I think the i2c_designware driver is at fault. With it disabled, performance improved very visibly, and estimated battery life increased by almost an hour. Time to file a bug report on Launchpad I think.

Thanks for the help y'all!

---

### Post by mewingatthemoon on 2021-06-04
For anyone interested, I've filed a bug against the linux-surface kernel:

[https://github.com/linux-surface/kernel/issues/101](https://github.com/linux-surface/kernel/issues/101)

Figure this has a better chance of actually getting it investigated and fixed upstream.

---

### Post by mewingatthemoon on 2021-07-04
So, an update. The problem is one of the I2C controllers. It's not exactly clear why, but that particular controller can be turned off without disabling the touchscreen via

```

# unbind INT33C2:00 to prevent interrupt spam 
echo INT33C2:00 > /sys/bus/i2c/devices/i2c-0/device/driver/unbind 

```

in rc.local, or somewhere else it will be run on boot. This may disable the power and volume buttons, but it preserves touch functionality.

---

