---
title: "Lucid heavy Hard Drive Usage"
date: 2010-06-18
forum: Hardware
---

### Post by abdusamed on 2010-06-18
I noticed something when my notebook is idling, i can hear my hardrive spinning much faster than it should be with the 'spin down hardrive' selected on from the power option. Because it's running fast, it my notebook become's pretty hot. Like working on a simple document, it's running fast and hot! Like right now...!
The thing can heat my keyboard alot.. much much hotter than windows 7...

---

### Post by abdusamed on 2010-06-18
Follow up this thread


[http://ubuntuforums.org/showthread.php?t=1506515](http://ubuntuforums.org/showthread.php?t=1506515)

---

### Post by abdusamed on 2010-06-19
Yea.. got it working after a bit 'bing'-ing :) around ubuntu forums. Turns out I had to 'manually' install 'laptop-mode' via synaptic manager which was default install in the previous ubuntu release -9.10. Now my hard drive runs MUCH cooler and does idle.. [idling right now while i'm typing this on gedit]. Before like i mentioned before it would only idel for a sec after I ran this command 
```

sudo hdparm -Y /dev/sda
```

But after installing 'laptop-mode' and editing the it's config file, it's HD running much like much quiter on ubuntu. I was suprise how really advance laptop-mode script really is like it's melted into the system though easy as heck to modify for one's need. Anyway, I edited the config to suite my style. Note- I only modified it for the state on battery, not on ac power. Below is my editied config, took a while but I did it. You can either read the entire code or you can read the manual which had everything explained very well and understandable 'newbie' language :)

To view it's manual simple run the below command AFTER you had install 'laptop-mode' in synaptic manager
```
man laptop-mode.conf 
``` 
It literally let's you control power manager in a level which is impossible on windows 7! 
Anyway, here's my code. I only changed the amount it buffer data, idling time, how long it can idle before it spins up my drive. I did my setting only for battery mode and laptop mode is on during that time.

Also, I would appreciate any modification which can further improve it. My next target is down volt on my cpu and gpu. Heard it can give me 1 hour boost like right now I was losing after 45mins of work time when I ran ubuntu instead of wins7. I don't know how much battery life i have gained after enabling laptop-mode but i'm sure i did gain something. HD are now also running much cooler on battery than they did before all thanks to laptop-mode. If I can down volt my notebook... I'm sure to cut 10+ degree of my notebook!! which would be just be great. I don't need performace when I'm on the go!

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

# Set this to 1 if you want to log messages to syslog
LOG_TO_SYSLOG=1

# Run in shell debug mode
# Enable this if you would like to execute the entire laptop-mode-tools program
# in shell debug mode. Warning: This will create a lot of text output
# If you are debugging an individual module, perhaps you would want to enable
# each module specific debug mode (available in module conf files)
DEBUG=0

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
ENABLE_LAPTOP_MODE_WHEN_LID_CLOSED=1



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
HD="/dev/sda /dev/sdb"


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
LM_BATT_MAX_LOST_WORK_SECONDS=1600
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
LM_READAHEAD=15072
NOLM_READAHEAD=128


#
# Should laptop mode tools add the "noatime" option to the mount options when 
# laptop mode is enabled?
#
CONTROL_NOATIME=1

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
LM_AC_HD_IDLE_TIMEOUT_SECONDS=20
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=5
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
CONTROL_HD_WRITECACHE=1


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
LM_DIRTY_RATIO=80
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

---

