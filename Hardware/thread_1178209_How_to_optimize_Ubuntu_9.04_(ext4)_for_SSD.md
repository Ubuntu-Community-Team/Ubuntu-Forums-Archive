---
title: "How to optimize Ubuntu 9.04 (ext4) for SSD?"
date: 2009-06-04
forum: Hardware
---

### Post by madsc89 on 2009-06-04
In a fedora forum, I found this list for SSD-optimalization. I've just baught a new laptop with a Kingston 80GB SSD (which is a rebranded Intel X25-M), and plan to install Ubuntu on it. Im going to run dual boot with W7 for games.
What I understand so far, is that I should use ext4 without journaling, and that I should do some other tweaks.
The question is: Which parts of this list should I do, What needs to be changed in order for it to work in Ubuntu, What can I skip, and is there anything else I should do?
> SSD Optimization
Perform the following if you’re using an SSD. If you’re using a hard drive you can skip this section.
Create Ramdisks to Store Frequently Written Areas

1. Edit your /etc/fstab file. Add the following lines.
tmpfs /var/log tmpfs defaults 0 0
tmpfs /tmp tmpfs defaults 0 0
tmpfs /var/tmp tmpfs defaults 0 0

Disable Access Time Attributes

1. Edit your /etc/fstab. Modify the root partitions settings. Add noatime and nodiratime to defaults.
/dev/sda2 / ext4 defaults,noatime,nodiratime 0 0

Optimizing the Kernel

1. Add the following to your /etc/rc.local file.
# Economize the SSD
sysctl -w vm.swappiness=1 # Strongly discourage swapping
sysctl -w vm.vfs_cache_pressure=50 # Don't shrink the inode cache aggressively

# As in the rc.last.ctrl of Linpus
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
cat /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate_max > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/sampling_rate

echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
echo 20 > /proc/sys/vm/dirty_ratio
echo 10 > /proc/sys/vm/dirty_background_ratio

echo 1 > /sys/devices/system/cpu/sched_smt_power_savings
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
echo 5 > /proc/sys/vm/laptop_mode

#Decrease power usage of USB while idle
[ -w /sys/bus/usb/devices/1-5/power/level ] && echo auto > /sys/bus/usb/devices/1-5/power/level
[ -w /sys/bus/usb/devices/5-5/power/level ] && echo auto > /sys/bus/usb/devices/5-5/power/level

/sbin/setpci -d 197b:2381 AE=47
/sbin/modprobe pciehp
/sbin/modprobe sdhci

Change the I/O Scheduler

1. Edit the /etc/grub.conf file. Add “elevator=noop” to the kernel line.
kernel /vmlinuz-2.6.27.5-117.fc10.i686 ro root=/dev/sda 
Source: [http://forums.fedoraforum.org/showthread.php?t=215109](http://forums.fedoraforum.org/showthread.php?t=215109)

I've run Ubuntu for a year now, but I'm still not completely sure on commands.

Thank you.

---

### Post by sam_delta on 2009-06-05
i would also want to know this,, i just bough an ssd, and installing in it soon.
i also read about partition aligning, does any1 know anything abou thtis? and how to do it?

Sam

---

### Post by sune_cph on 2009-06-19
>1. Edit your /etc/fstab file. Add the following lines.
>tmpfs /var/log tmpfs defaults 0 0
>tmpfs /tmp tmpfs defaults 0 0
>tmpfs /var/tmp tmpfs defaults 0 0

If you're going to put all your log files in tmpfs to prevent writing to the SSD, you might as well put your ~/.xsession-errors in tmpfs too.

One way to do this, is to move .xsession-errors to /tmp (which is in tmpfs if use the settings above):

$ sudo chown root:root .xsession-errors
$ sudo chattr +i .xsession-errors

This will effectively create a new (randomly named) .xsession-errors file in /tmp because the default $HOME/.xsession-errors is no longer writeable.

Works for me :-)

/Sune

---

### Post by Ruhani04 on 2009-06-19
I know this thread is not the latest but I would recommend checking the following from the OCZ forum:

[http://www.ocztechnologyforum.com/forum/showthread.php?t=54379&highlight=linux](http://www.ocztechnologyforum.com/forum/showthread.php?t=54379&highlight=linux)

It is very technical but I set up my SSD with Ubuntu 9.04 accordingly and I must say it runs a lot faster than my velociraptor on a desktop.
Had no problems so far.
Good luck.

---

### Post by xjgnsdof on 2009-10-18
Do any of these tweaks apply to Karmic beta?

---

### Post by sune_cph on 2009-10-23
> **elgilicious said:**
> Do any of these tweaks apply to Karmic beta?

Most of these tweaks are pretty "generic", such as moving temporary files and logs to tmpfs (in ram) instead of ssd so they would apply to any linux distro.

/Sune

---

### Post by Yahoé on 2012-10-09
It is clear that /var/tmp should not be in tmpfs since by definition it's content needs to be preserved beyond reboots:
[http://linuxers.org/article/differences-between-tmp-and-vartmp](http://linuxers.org/article/differences-between-tmp-and-vartmp)

---

### Post by matt_symes on 2012-10-09
Very old thread so closed.

---

