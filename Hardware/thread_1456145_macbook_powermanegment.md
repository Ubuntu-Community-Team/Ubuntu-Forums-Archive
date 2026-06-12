---
title: "macbook powermanegment"
date: 2010-04-16
forum: Hardware
---

### Post by Dans564 on 2010-04-16
new mint install on white macbook does not recognise my laptop battery.  It does not show up in power management or the tray icon.

When I use the command, "sudo /usr/sbin/laptop_mode status" this is the output:

Mounts:
   /dev/sda2 on / type ext4 (rw,errors=remount-ro)
   proc on /proc type proc (rw)
   none on /sys type sysfs (rw,noexec,nosuid,nodev)
   none on /sys/fs/fuse/connections type fusectl (rw)
   none on /sys/kernel/debug type debugfs (rw)
   none on /sys/kernel/security type securityfs (rw)
   udev on /dev type tmpfs (rw,mode=0755)
   none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
   none on /dev/shm type tmpfs (rw,nosuid,nodev)
   none on /var/run type tmpfs (rw,nosuid,mode=0755)
   none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
   none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
   binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
   gvfs-fuse-daemon on /home/dan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dan)

Drive power status:
   
   /dev/sda:
    drive state is:  active/idle

(NOTE: drive settings affected by Laptop Mode cannot be retrieved.)

Readahead states:
   /dev/sda2: 128 kB

Laptop Mode Tools is NOT allowed to run: /var/run/laptop-mode-tools/enabled does not exist.

/proc/sys/vm/laptop_mode:
   0

/proc/sys/vm/dirty_ratio:
   20

/proc/sys/vm/dirty_background_ratio:
   10

/proc/sys/vm/dirty_expire_centisecs:
   3000

/proc/sys/vm/dirty_writeback_centisecs:
   500

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq:
   1000000

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq:
   1833000

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq:
   1000000

/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq:
   1000000

/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_max_freq:
   1833000

/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_min_freq:
   1000000

/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:
   ondemand

/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:
   ondemand

/proc/acpi/button/lid/LID0/state:
   state:      open

/proc/acpi/ac_adapter/ADP1/state:
   state:                   on-line

/proc/acpi/battery/BAT0/state:
   present:                 yes
   capacity state:          ok
   charging state:          charging
   present rate:            28181 mW
   remaining capacity:      15760 mWh
   present voltage:         11655 mV

/sys/class/power_supply/ADP1/online:

---

### Post by Dans564 on 2010-04-16
anybody?!?!?  
Usually this forum is super fast :(

---

