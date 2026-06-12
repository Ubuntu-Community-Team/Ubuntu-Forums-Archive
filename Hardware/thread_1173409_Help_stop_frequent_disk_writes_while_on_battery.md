---
title: "Help stop frequent disk writes while on battery"
date: 2009-05-29
forum: Hardware
---

### Post by m4cph1sto on 2009-05-29
My hard drive spins up every minute or so on battery due to disk writes by various processes.  I'm trying to get these programs to stop writing to disk all the time.  I'm using Jaunty with laptop-mode enabled. Here's a typical iotop output (polling every 10 seconds).   

```

$ iotop -o -d 10 -b
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 6.76 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 3853 david          0 B/s    0.40 K/s  0.00 %  0.00 % gnome-power-manager
 1960 root           0 B/s    6.37 K/s  0.00 %  0.00 % [kjournald2]
Total DISK READ: 0 B/s | Total DISK WRITE: 2.79 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 3853 david          0 B/s    0.40 K/s  0.00 %  0.00 % gnome-power-manager
 1960 root           0 B/s    2.39 K/s  0.00 %  0.00 % [kjournald2]
Total DISK READ: 0 B/s | Total DISK WRITE: 3.18 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 1960 root           0 B/s    3.18 K/s  0.00 %  0.00 % [kjournald2]
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 1.19 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 2359 syslog         0 B/s    1.19 K/s  0.00 %  0.00 % syslogd -u syslog
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0.40 K/s | Total DISK WRITE: 7.16 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
  717 root           0 B/s    1.19 K/s  0.00 %  0.00 % [kjournald2]
 3853 david       0.40 K/s    0.40 K/s  0.00 %  0.00 % gnome-power-manager
 1960 root           0 B/s    5.57 K/s  0.00 %  0.00 % [kjournald2]
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 1.19 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 2840 root           0 B/s    1.19 K/s  0.00 %  0.00 % winbindd
Total DISK READ: 0 B/s | Total DISK WRITE: 0.40 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 3853 david          0 B/s    0.40 K/s  0.00 %  0.00 % gnome-power-manager
Total DISK READ: 0 B/s | Total DISK WRITE: 6.37 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
   22 root           0 B/s    0.40 K/s  0.00 %  0.00 % [pdflush]
  717 root           0 B/s    0.40 K/s  0.00 %  0.00 % [kjournald2]
 1960 root           0 B/s    5.57 K/s  0.00 %  0.00 % [kjournald2]
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 2.78 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 3853 david          0 B/s    0.40 K/s  0.00 %  0.00 % gnome-power-manager
 1960 root           0 B/s    2.39 K/s  0.00 %  0.00 % [kjournald2]
Total DISK READ: 0 B/s | Total DISK WRITE: 3.18 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 1960 root           0 B/s    3.18 K/s  0.00 %  0.00 % [kjournald2]
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
Total DISK READ: 0 B/s | Total DISK WRITE: 1.19 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
 2359 syslog         0 B/s    1.19 K/s  0.00 %  0.00 % syslogd -u syslog
Total DISK READ: 0 B/s | Total DISK WRITE: 3.98 K/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO    COMMAND
  717 root           0 B/s    1.19 K/s  0.00 %  0.00 % [kjournald2]
 3853 david          0 B/s    0.40 K/s  0.00 %  0.00 % gnome-power-manager
 1960 root           0 B/s    2.39 K/s  0.00 %  0.00 % [kjournald2]

```

The culprits are gnome-power-manager, "syslogd -u syslog", winbindd, and pdflush. 

I'm guessing I can reduce writes from pdflush by tweaking my laptop-mode.conf, but I don't know which settings to change.  

For syslogd, I've used the option 

CONTROL_CONFIG_FILES=1

in /etc/laptop-mode/conf.d/configuration-file-control.conf to create separate syslog.conf files for AC and battery operation, and I've tried to modify them so that logging will be disabled on battery, but apparently syslogd is still writing something.  How do I get it to stop completely?

As for gnome-power-manager, it is by far doing the most disk writes (not good for a power manager!), and I don't know how to get it to stop, short of killing the process.  Any advice?

I don't even know what winbindd is.  Should I just kill it?

Below are my relevant config files:

laptop-mode.conf:
```

###############################################################################
#
# Configuration for Laptop Mode Tools
# -----------------------------------
#
# There is a "system" to the configuration setting names:
#    CONTROL_something=0/1   Determines whether Laptop Mode Tools controls 
#                            something
#    LM_something=value      Value of "something" when laptop mode is active
#    NOLM_something=value    Value of "something" when laptop mode is NOT
#                            active
#    AC_something=value      Value of "something" when the computer is running
#                            on AC power
#    BATT_something=value    Value of "something when the computer is running
#                            on battery power
#
# There can be combinations of LM_/NOLM_ and AC_/BATT_ prefixes, but the
# available prefixes are different for each setting. The available ones are 
# documented in the manual page, laptop-mode.conf(8). If there is no LM_/
# NOLM_ in a setting name, then the value is used independently of laptop
# mode state, and similarly, if there is no AC_/BATT_, then the value is used
# independently of power state.
#
# Some options only work on ACPI systems. They are marked ACPI-ONLY.
#
# Note that this configuration file is a fragment of shell script: you
# can use all the features of the shell scripting language to achieve your
# desired configuration.
#
# 
# Modules
# -------
#
# Laptop Mode Tools modules have separate configuration files, that can be
# found in /etc/laptop-mode/conf.d. Please look through these configuration
# files as well, there are many useful power saving tools in there!
#
###############################################################################



###############################################################################
# Configuration debugging
# -----------------------
###############################################################################


#
# Set this to 1 if you want to see a lot of information when you start/stop 
# laptop_mode.
#
VERBOSE_OUTPUT=0



###############################################################################
# When to enable laptop mode
# --------------------------
#
# "Laptop mode" is the mode in which laptop mode tools makes the computer
# consume less power. This includes the kernel "laptop_mode" feature, which
# allows your hard drives to spin down, as well as various other settings which
# can be tweaked by laptop mode tools. You can enable or disable all of these
# settings using the CONTROL_... options further down in this config file.
###############################################################################


#
# Enable laptop mode when on battery power.
#
ENABLE_LAPTOP_MODE_ON_BATTERY=1


#
# Enable laptop mode when on AC power.
#
ENABLE_LAPTOP_MODE_ON_AC=0


#
# Enable laptop mode when the laptop's lid is closed, even when we're on AC
# power? (ACPI-ONLY)
#
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=0



###############################################################################
# When to enable data loss sensitive features
# -------------------------------------------
#
# When data loss sensitive features are disabled, laptop mode tools acts as if
# laptop mode were disabled, for those features only.
#
# Data loss sensitive features include:
# - laptop_mode (i.e., delayed writes)
# - hard drive write cache
#
# All of the options that follow can be set to 0 in order to prevent laptop
# mode tools from using them to stop data loss sensitive features. Use this
# when you have a battery that reports the wrong information, that confuses
# laptop mode tools.
#
# Disabling data loss sensitive features is ACPI-ONLY, and it only works if
# your battery gives off frequent ACPI events to indicate a change in battery
# level.
#
# NOTE: If your battery does NOT give off battery events often enough, you can
# enable the battery-level-polling module to make this work. Look at the
# file /etc/laptop-mode/conf.d/battery-level-polling.conf for more information.
#
###############################################################################


#
# Disable all data loss sensitive features when the battery level (in % of the
# battery capacity) reaches this value.
#
MINIMUM_BATTERY_CHARGE_PERCENT=3


#
# Disable data loss sensitive features when the battery reports its state
# as "critical".
#
DISABLE_LAPTOP_MODE_ON_CRITICAL_BATTERY_LEVEL=1



###############################################################################
# Controlled hard drives and partitions
# -------------------------------------
#
# For spinning down your hard drives, laptop mode will remount file systems and
# adjust hard drive spindown timeouts. These parameters specify which
# devices and partitions are affected by laptop mode.
###############################################################################


#
# The drives that laptop mode controls.
# Separate them by a space, e.g. HD="/dev/hda /dev/hdb". The default is a
# wildcard, which will get you all your IDE and SCSI/SATA drives.
#
HD="/dev/[hs]d[abcdefgh]"


#
# The partitions (or mount points) that laptop mode controls.
# Separate the values by spaces. Use "auto" to indicate all partitions on drives
# listed in HD. You can add things to "auto", e.g. "auto /dev/hdc3". You can
# also specify mount points, e.g. "/mnt/data".
#
PARTITIONS="auto /dev/mapper/*"


#
# If this is enabled, laptop mode tools will assume that SCSI drives are
# really SATA drives that only _look_ like SCSI drives, and will use hdparm
# to control them. Set this to 0 if you have /dev/sd devices and you want
# laptop mode tools to use the "sdparm" command to control them. 
#
ASSUME_SCSI_IS_SATA=1


###############################################################################
# Hard drive behaviour settings
# -----------------------------
#
# These settings specify how laptop mode tools will adjust the various
# parameters of your hard drives and file systems.
###############################################################################


#
# Maximum time, in seconds, of work that you are prepared to lose when your
# system crashes or power runs out. This is the maximum time that Laptop Mode
# will keep unsaved data waiting in memory before spinning up your hard drive.
#
LM_BATT_MAX_LOST_WORK_SECONDS=600
LM_AC_MAX_LOST_WORK_SECONDS=360


#
# Should laptop mode tools control readahead?
#
CONTROL_READAHEAD=1


#
# Read-ahead, in kilobytes. You can spin down the disk while playing MP3/OGG
# by setting the disk readahead to a reasonable size, e.g. 3072 (3 MB).
# Effectively, the disk will read a complete MP3 at once, and will then spin 
# down while the MP3/OGG is playing. Don't set this too high, because the 
# readahead is applied to _all_ files that are read from disk.
#
LM_READAHEAD=3072
NOLM_READAHEAD=128


#
# Should laptop mode tools add the "noatime" option to the mount options when 
# laptop mode is enabled?
#
CONTROL_NOATIME=0

# Should laptop use relatime instead of noatime? The "relatime" mount option has
# more standards-compliant semantics, and allows more applications to work,
# while retaining a low level of atime updates (i.e., disk writes).
USE_RELATIME=1


#
# Should laptop mode tools control the hard drive idle timeout settings?
#
CONTROL_HD_IDLE_TIMEOUT=1


#
# Idle timeout values. (hdparm -S)
# Default is 2 hours on AC (NOLM_HD_IDLE_TIMEOUT_SECONDS=7200) and 20 seconds
# for battery and for AC with laptop mode on.
#
LM_AC_HD_IDLE_TIMEOUT_SECONDS=60
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=60
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200


#
# Should laptop mode tools control the hard drive power management settings?
#
CONTROL_HD_POWERMGMT=1


#
# Power management for HD (hdparm -B values)
#
BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=254
NOLM_AC_HD_POWERMGMT=254


#
# Should laptop mode tools control the hard drive write cache settings?
#
CONTROL_HD_WRITECACHE=0


#
# Write cache settings for HD (hdparm -W values)
#
NOLM_AC_HD_WRITECACHE=1
NOLM_BATT_HD_WRITECACHE=0
LM_HD_WRITECACHE=0




###############################################################################
# Settings you probably don't want to touch
# -----------------------------------------
#
# It is usually not necessary to change these parameters. They are included
# for completeness' sake.
###############################################################################


#
# Change mount options on partitions in PARTITIONS? You don't really want to
# disable this. If you do, then your hard drives will probably not spin down
# anymore.
#
CONTROL_MOUNT_OPTIONS=1


#
# Dirty synchronous ratio.  At this percentage of dirty pages the process
# which calls write() does its own writeback.
#
LM_DIRTY_RATIO=60
NOLM_DIRTY_RATIO=40


#
# Allowed dirty background ratio, in percent.  Once DIRTY_RATIO has been
# exceeded, the kernel will wake pdflush which will then reduce the amount
# of dirty memory to dirty_background_ratio.  Set this nice and low, so once
# some writeout has commenced, we do a lot of it.
#
LM_DIRTY_BACKGROUND_RATIO=1
NOLM_DIRTY_BACKGROUND_RATIO=10


#
# kernel default settings -- don't touch these unless you know what you're 
# doing.
#
DEF_UPDATE=5
DEF_XFS_AGE_BUFFER=15
DEF_XFS_SYNC_INTERVAL=30
DEF_XFS_BUFD_INTERVAL=1
DEF_MAX_AGE=30


#
# This must be adjusted manually to the value of HZ in the running kernel
# on 2.4, until the XFS people change their 2.4 external interfaces to work in
# centisecs. This can be automated, but it's a work in progress that still
# needs some fixes. On 2.6 kernels, XFS uses USER_HZ instead of HZ for
# external interfaces, and that is currently always set to 100. So you don't
# need to change this on 2.6.
#
XFS_HZ=100


#
# Seconds laptop mode has to to wait after the disk goes idle before doing
# a sync.
#
LM_SECONDS_BEFORE_SYNC=2

```

/etc/syslog.conf-batt:
```

#  /etc/syslog.conf	Configuration file for syslogd.
#
#			For more information see syslog.conf(5)
#			manpage.

#
# First some standard logfiles.  Log by facility.
#

auth,authpriv.*			-/var/log/auth.log
*.*;auth,authpriv.none		-/var/log/syslog
#cron.*				-/var/log/cron.log
daemon.*			-/var/log/daemon.log
kern.*				-/var/log/kern.log
lpr.*				-/var/log/lpr.log
mail.*				-/var/log/mail.log
user.*				-/var/log/user.log

#
# Logging for the mail system.  Split it up so that
# it is easy to write scripts to parse these files.
#
mail.info			-/var/log/mail.info
mail.warning			-/var/log/mail.warn
mail.err			-/var/log/mail.err

# Logging for INN news system
#
news.crit			-/var/log/news/news.crit
news.err			-/var/log/news/news.err
news.notice			-/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
	auth,authpriv.none;\
	news.none;mail.none	-/var/log/debug
*.=info;*.=notice;*.=warning;\
	auth,authpriv.none;\
	cron,daemon.none;\
	mail,news.none		-/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg				*

#
# I like to have messages displayed on the console, but only on a virtual
# console I usually leave idle.
#
#daemon,mail.*;\
#	news.=crit;news.=err;news.=notice;\
#	*.=debug;*.=info;\
#	*.=notice;*.=warning	/dev/tty8

# The named pipe /dev/xconsole is for the `xconsole' utility.  To use it,
# you must invoke `xconsole' with the `-file' option:
# 
#    $ xconsole -file /dev/xconsole [...]
#
# NOTE: adjust the list below, or you'll go crazy if you have a reasonably
#      busy site..
#
daemon.*;mail.*;\
	news.err;\
	*.=debug;*.=info;\
	*.=notice;*.=warning	|/dev/xconsole

```

Any help in getting the above-mentioned processes to stop writing to disk all the time would be greatly appreciated!

---

### Post by kidders on 2009-05-31
Hi there,

I've never used Linux in laptop mode, but since your post has gone unanswered for a whole day, I might as well give it a shot ...

As you probably know, syslogd often explicitly syncs disk writes, because when a computer crashes, log messages are invariably the first place to look for the cause. If they were still in memory at the time of the crash, you'd have nothing to go on. I suspect your syslogd configuration isn't being swapped out for the one you posted, with the "-" characters before all the filenames.

As far as I can tell from a little Googling, setting CONTROL_CONFIG_FILES isn't enough to reconfigure & restart syslog. For example, you don't seem to specify *which* config files to manage. Does that seem sensible?

Regarding other processes, you may find that you can't stop absolutely everything from using fsync() calls ... their config files may not give you a way to tell them not to. In those cases, I would suggest filing a bug with the developer ... at worst, they'll tell you why the explicit sync is too important to take out.

Incidentally, winbindd provides an alternate source of name resolution to your box. Not using it may adversely affect name resolution where the only source of the information is a Windows NT box. If you're not interested in talking to Windows machines, you can certainly disable it. Even if you are, you may still get along perfectly well without it though.

Anyhow, I hope that helps. If I'm on the wrong track with your laptop-mode.conf, be sure to post back & yell at me!

---

### Post by m4cph1sto on 2009-06-01
Thanks for your response.  I've disabled winbindd, we'll see if it has any detrimental effects.  Gnome-power-manager is the big problem.  I found an old bug report and re-opened it:

[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/315970](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/315970)

This user reported that gnome-power-manager writes what looks like actual state of battery to $HOME/.gnome2/gnome-power-manager about every 90 seconds.  This is probably the same thing I'm seeing.  Perhaps there's a config setting for g-p-m to change this behavior?

I'll keep working on the syslog settings and post when I have some success.

---

### Post by m4cph1sto on 2009-06-01
I just posted to the bug report, I can confirm that about every 90 seconds gnome-power-manager is writing to the file:

$/HOME/.gnome2/gnome-power-manager/profile-G71C0001W210-38880-0000000193-discharging.csv

This is shortening battery life and could lead to early hard drive failure, all for the purpose of providing a nifty discharge-time profile.  I wonder if this "feature" can be disabled completely, or at least change the write-time from 90 seconds to something reasonable, say 10 or 20 minutes.

---

