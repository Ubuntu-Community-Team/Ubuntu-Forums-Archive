---
title: "Hibernation doesn't work at all"
date: 2016-05-15
forum: Hardware
---

### Post by trappo on 2016-05-15
After 16.04 clean install hibernation doesn't work at all. 
Launching pm-hibernate as root i get no output and nothing happens.
After:
```

export PM_DEBUG=true
pm-hibernate
```
i get this:
```

+ set -a
+ PM_UTILS_LIBDIR=/usr/lib/pm-utils
+ PM_UTILS_ETCDIR=/etc/pm
+ PM_UTILS_RUNDIR=/var/run/pm-utils
+ PATH=/sbin:/usr/sbin:/bin:/usr/bin:/usr/lib/pm-utils/bin
+ PM_LOGFILE=/var/log/pm-suspend.log
+ TEMPORARY_CPUFREQ_GOVERNOR=performance
+ LOCKDIR=/var/run/pm-utils/locks
+ STORAGEDIR=/var/run/pm-utils/pm-suspend/storage
+ NA=254
+ NX=253
+ DX=252
+ PM_FUNCTIONS=/usr/lib/pm-utils/functions
+ PM_QUIRKDB=/usr/lib/pm-utils/video-quirks
+ PM_LKW_QUIRKS=/var/cache/pm-utils/last_known_working.quirkdb
+ LC_COLLATE=C
+ HIBERNATE_MODE=
+ HIBERNATE_RESUME_POST_VIDEO=no
+ SLEEP_MODULE=auto
+ SUSPEND_MODULES=
+ HOOK_BLACKLIST=
+ ADD_PARAMETERS=
+ DROP_PARAMETERS=
+ PARAMETERS=/var/run/pm-utils/pm-suspend/storage/parameters
+ INHIBIT=/var/run/pm-utils/pm-suspend/storage/inhibit
+ PM_CMDLINE=
+ BEFORE_HOOKS=
+ MODULE_HELP=
+ SUSPEND_MODULE=
+ HIBERNATE_MODULE=
+ SUSPEND_HYBRID_MODULE=
+ PM_HIBERNATE_DELAY=900
+ PM_RTC=/sys/class/rtc/rtc0
+ [ -f /usr/lib/pm-utils/defaults ]
+ . /usr/lib/pm-utils/defaults
+ [ -f /usr/lib/pm-utils/pm-suspend.defaults ]
+ set +a
+ [ -f /etc/pm/config.d/*[!~] ]
+ continue
+ [ -f /etc/pm/pm-suspend.config.d/*[!~] ]
+ continue
+ . /usr/lib/pm-utils/functions
+ is_set true
+ return 0
+ set -x
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ profiling
+ [  = true ]
+ [ auto = auto ]
+ SLEEP_MODULE=tuxonice uswsusp
+ mod=/usr/lib/pm-utils/module.d/tuxonice
+ [ -f /usr/lib/pm-utils/module.d/tuxonice ]
+ . /usr/lib/pm-utils/module.d/tuxonice
+ export TUXONICE_LOC
+ [ -d /sys/power/tuxonice ]
+ [ -d /sys/power/suspend2 ]
+ [ -n  ]
+ [ -z  -a -n  ]
+ [ -z  -a -n  ]
+ mod=/usr/lib/pm-utils/module.d/uswsusp
+ [ -f /usr/lib/pm-utils/module.d/uswsusp ]
+ . /usr/lib/pm-utils/module.d/uswsusp
+ [ -z  ]
+ command_exists s2ram
+ type s2ram
+ return 0
+ grep -q mem /sys/power/state
+ SUSPEND_MODULE=uswsusp
+ [ hibernate = suspend ]
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -z  ]
+ grep -q mem /sys/power/state
+ command_exists s2both
+ type s2both
+ return 0
+ check_hibernate
+ [ -n  ]
+ [ -z uswsusp ]
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -z  ]
+ [ -f /sys/power/disk ]
+ grep -q disk /sys/power/state
+ [ -z  -a -w /sys/class/rtc/rtc0/wakealarm ]
+ check_suspend
+ [ -n uswsusp ]
+ check_hibernate
+ [ -n  ]
+ r=0
+ id -u
+ [ 0 != 0 ]
+ try_lock pm-suspend.lock
+ local lock=/var/run/pm-utils/locks/pm-suspend.lock
+ mkdir -p /var/run/pm-utils/locks
+ touch /var/run/pm-utils/locks/pm-suspend.lock
+ exec
+ flock -x -n 3
+ return 0
+ trap remove_suspend_lock 0
+ rm -rf /var/run/pm-utils/pm-suspend/storage
+ mkdir -p /var/run/pm-utils/pm-suspend/storage
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters ]
+ echo 
+ add_parameters
+ remove_parameters
+ local p
+ [  = all ]
+ echo 
+ grep -vxFf /var/run/pm-utils/pm-suspend/storage/parameters.rm /var/run/pm-utils/pm-suspend/storage/parameters
+ cp -f /var/run/pm-utils/pm-suspend/storage/parameters.new /var/run/pm-utils/pm-suspend/storage/parameters
+ update_parameters
+ [ -f /var/run/pm-utils/pm-suspend/storage/parameters.new ]
+ get_parameters
+ cat /var/run/pm-utils/pm-suspend/storage/parameters
+ export PM_CMDLINE=
+ rm -f /var/run/pm-utils/pm-suspend/storage/parameters.new
+ [ 0 -gt 0 ]
+ command_exists check_hibernate
+ type check_hibernate
+ return 0
+ command_exists do_hibernate
+ type do_hibernate
+ return 127
+ log pm-utils does not know how to hibernate on this system.
+ is_set 
+ return 2
+ return 0
+ exit 1
+ remove_suspend_lock
+ release_lock pm-suspend.lock
+ local lock=/var/run/pm-utils/locks/pm-suspend.lock
+ rm -f /var/run/pm-utils/locks/pm-suspend.lock
+ return 0

```
What shall I do?

---

