---
title: "HDD load/unload cycles too frequent on ubuntu 11.04"
date: 2011-12-13
forum: Hardware
---

### Post by sidell on 2011-12-13
Hi,

I believed this problem ([Bug #59695]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695")) was solved since a long time. But today, I installed ubuntu 11.10 and on battery I have a too high frequency of load/unload cycle on my hard disk. I can heard the noise of my hard disk every 4 seconds approx.

Why this bug is not yet fixed and what is now the proper manner to do this?
**    **

---

### Post by sidell on 2011-12-18
up :(

---

### Post by Toz on 2011-12-19
I had a similar problem with one of my laptops when going to battery mode. acpi was putting the hard drive into power-saving mode, hence parking the drive heads frequently and creating the clicking sound. Here is how I fixed it:

From /usr/lib/pm-utils/power.d/95hdparm-apm
```

if grep -wq "nohdparm" /proc/cmdline ; then
   exit 0
fi
```

Meaning that if **nohdparm** exists in your kernel commandline, this script (the one that initiates the hard drive power-saving mode) isn't executed. So, I added **nohdparm** to my kernel command line and the power-saving features weren't enabled and the clicking stopped.

---

### Post by sidell on 2011-12-19
thanks.

Did you notice a change in the battery life?

---

### Post by Toz on 2011-12-19
> **sidell said:**
> thanks.

Did you notice a change in the battery life?
Not really. I was only looking to stop the annoying clicking sound.

---

### Post by sidell on 2011-12-22
In fact, adding nohdparm to the kernel lign do not fix entirely the problem for me. I have still some parking but less frequently.

```
pierre@nil:~$ sudo smartctl -a $(mount | sed -n '/\/ /s/[0-9].*//p') | grep 'Cycle\|Power' && date
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1459
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1347
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       71
193 Load_Cycle_Count        0x0032   197   197   000    Old_age   Always       -       10349
Thu Dec 22 12:02:55 CET 2011
pierre@nil:~$ sudo smartctl -a $(mount | sed -n '/\/ /s/[0-9].*//p') | grep 'Cycle\|Power' && date
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1459
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1347
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       71
193 Load_Cycle_Count        0x0032   197   197   000    Old_age   Always       -       10350
Thu Dec 22 12:03:01 CET 2011

```If I launch the command :```
 sudo hdparm -B 154 /dev/sda
``` I have no parking at all but I don't know how ta make this command permanent. I tried this ```
cmd='hdparm -B 254 /dev/sda';sudo $cmd && echo -e '#!/bin/sh\n'"$cmd" > /tmp/hdfix && sudo install /tmp/hdfix /etc/pm/power.d/00-hdparm.sh && sudo install /tmp/hdfix /etc/pm/sleep.d/00-hdparm.sh
``` But it's not working in ubuntu 11.10.

---

### Post by Toz on 2011-12-22
Instead of */etc/pm/sleep.d/[COLOR="Red"]00[/COLOR]-hdparm.sh*, try naming the file **/etc/pm/sleep.d/[COLOR="Red"]99[/COLOR]-hdparm.sh**. That way it will be executed last (in case something else is resetting the value through the process)

---

### Post by sidell on 2011-12-23
Thanks it works!

---

