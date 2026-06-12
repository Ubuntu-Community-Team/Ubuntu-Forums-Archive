---
title: "Laptop-Mode Settings"
date: 2007-02-25
forum: Hardware &amp; Laptops
---

### Post by cb474 on 2007-02-25
I don't understand this section of the laptop-mode settings:

> ###############################################################################
# X display settings
# ------------------
#
# Using these settings, you can let laptop mode tools control the X display
# standby timeouts.
###############################################################################

# Should laptop mode tools control DPMS standby settings for X displays?
CONTROL_DPMS_STANDBY=0

# These settings specify the standby timeout for the X display,
# in seconds. The suspend and poweroff timeouts are somewhat
# larger values derived from these values.
BATT_DPMS_STANDBY=300
LM_AC_DPMS_STANDBY=1200
NOLM_AC_DPMS_STANDBY=1200

Does the last paragraph mean that once you enable laptop-mode to control dpms standby, it is also going to automatically suspend and shut down the computer, after an amount of time it determines (based on the standby settings)?

I just want laptop-mode to turn the display off, I don't want it to suspend and shutdown my computer.



Also, could someone go over and explain the hard drive behaviour settings (below), I really don't understand them and the effects they have, and can't find any good explanations online.

I would like my hard drive to spin down after thirty seconds or so and not spin up constantly, when the system writes to the hard drive for whatever it's doing. But when I got to deliberately save a file, I want the hard drives to spin up. So I don't really like the LOST_WORK_SECONDS setting here, because nothing gets saved to disk when I deliberately save a file.

> ###############################################################################
# Hard drive behaviour settings
# -----------------------------
#
# These settings specify how laptop mode tools will adjust the various
# parameters of your hard drives and file systems.
###############################################################################

# Maximum time, in seconds, of work that you are prepared to lose when your
# system crashes or power runs out. This is the maximum time that Laptop Mode
# will keep unsaved data waiting in memory before spinning up your hard drive.
LM_BATT_MAX_LOST_WORK_SECONDS=0
LM_AC_MAX_LOST_WORK_SECONDS=0

# Should laptop mode tools control readahead?
CONTROL_READAHEAD=1

# Read-ahead, in kilobytes. You can spin down the disk while playing MP3/OGG
# by setting the disk readahead to a reasonable size, e.g. 3072 (3 MB).
# Effectively, the disk will read a complete MP3 at once, and will then spin 
# down while the MP3/OGG is playing. Don't set this too high, because the 
# readahead is applied to _all_ files that are read from disk.
LM_READAHEAD=3072
NOLM_READAHEAD=128

# Should laptop mode tools add the "noatime" option to the mount options when 
# laptop mode is enabled?
CONTROL_NOATIME=0

# Should laptop mode tools control the hard drive idle timeout settings?
CONTROL_HD_IDLE_TIMEOUT=1

# Idle timeout values. (hdparm -S)
# Default is 2 hours on AC (NOLM_HD_IDLE_TIMEOUT_SECONDS=7200) and 5 seconds
# for battery and for AC with laptop mode on.
LM_AC_HD_IDLE_TIMEOUT_SECONDS=30
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=120
NOLM_HD_IDLE_TIMEOUT_SECONDS=7200

# Should laptop mode tools control the hard drive power management settings?
CONTROL_HD_POWERMGMT=0

# Power management for HD (hdparm -B values)
BATT_HD_POWERMGMT=1
LM_AC_HD_POWERMGMT=255
NOLM_AC_HD_POWERMGMT=255

# Should laptop mode tools control the hard drive write cache settings?
CONTROL_HD_WRITECACHE=0

# Write cache settings for HD (hdparm -W values)
NOLM_AC_HD_WRITECACHE=1
NOLM_BATT_HD_WRITECACHE=0
LM_HD_WRITECACHE=0


Thanks

---

### Post by Richard Kut on 2007-02-27
man laptop-mode.conf

---

### Post by lavinog on 2007-02-27
> I just want laptop-mode to turn the display off, I don't want it to suspend and shutdown my computer.

Why? Just curious.
Are you using Ubuntu?
what if you just set the *sleep type when inactive* to suspend instead of hibernate using the power management.
system>preferences>power management
under the general tab.

---

