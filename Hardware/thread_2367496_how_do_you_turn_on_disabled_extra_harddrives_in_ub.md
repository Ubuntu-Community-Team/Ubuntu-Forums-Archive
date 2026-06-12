---
title: "how do you turn on disabled extra harddrives in ubuntu?"
date: 2017-07-31
forum: Hardware
---

### Post by sammy11 on 2017-07-31
I have a computer that has two hard drives one is for storage the other windows OS now I want to swith over to linux ubuntu and be able to disable the storage hard drive like I can in windws how do I do that in linux ubuntu?

---

### Post by Autodave on 2017-07-31
I am confused: are you trying to enable or disable a HD? Are you keeping Windows on the machine or removing it? What version of Windows are you running?

---

### Post by Bucky Ball on 2017-07-31
Welcome. As above. Can you give more detail about what you intend to put where and what exactly you are up to? Are you keeping Windows? Where do you intend installing Ubuntu? Which release and flavour? You want to disable the drive BEFORE you install Ubuntu or after?

If before, you could just unplug it. If after, you either remove or comment out the line that boots the drive from the Ubuntu boot file (/etc/fstab).

---

### Post by cariboo on 2017-07-31
Like Bucky Ball said, just don't mount the drive on boot. If the drive isn't mounted, no one can access it.

---

### Post by efflandt on 2017-07-31
**sudo hdparm** (or as root scripts) based on command line options can put a drive into **standby** (which spins it down, but can wake up if accessed) or deeper **sleep** mode which does not wake up without a reset or reboot. This is an example of a script I put in /etc/cron.hourly to spin down my Win7 and Ubuntu 14.04 drive (sda) if it is not mounted or already in standby, while running a newer Ubuntu version from SSD (sdb). The drive still wakes up and automounts if I click on a partition on the drive in file manager (nautilus):```
#!/bin/sh
# Spin down drive(s) when idle and not mounted
# Put script in /etc/cron.hourly
drives="/dev/sda" # drive(s) to spin down (space separated)
IFS="$(printf '\n\t')" # remove newline from hdparm output
for hd in $drives
do
  dstate=$(/sbin/hdparm -C $hd | /bin/grep -B 1 standby)
  if [ $? -ne 0 ] # if not in standby
  then # active/idle
    /bin/grep $hd /etc/mtab 2>&1 > /dev/null
    if [ $? -ne 0 ] # do standby if not mounted
    then dstate=$(/sbin/hdparm -y $hd 2>&1)
    fi 
  fi
  if [ "$dstate" != '' ] # log unless mounted (null)
    then echo $dstate | /usr/bin/logger -e
  fi
done
```

---

### Post by johndough2 on 2017-08-01
Hi

If the drive is to be disabled in both/all scenarios, then remove it and save on the energy and possibly extend it's life.

---

