---
title: "hibernate, hal, acpi... oh my!"
date: 2008-02-10
forum: Hardware &amp; Laptops
---

### Post by ehula on 2008-02-10
I am running Gutsy Gibbon with the latest Zen kernel (with Suspend2/Tuxonice) and have installed the latest hibernate script package. I am able to hibernate and resume successfully with a "sudo hibernate", but cannot by using my laptop's keyboard shortcut (Fn-F12 on an IBM Thinkpad T43p) nor by selecting "hibernate" from the Gnome log-off options. I am assuming there is something that needs to be configured in one of the following files. Can someone please look at these files and suggest some edits. I have modified these files over the course of many Ubuntu versions, so they may need replacing with the default files (where could I get defaults?):

/etc/acpi/hibernate.sh
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs
. /usr/share/acpi-support/policy-funcs

if [ x$HIBERNATE_SCRIPT = xtrue ] && [ -x /usr/local/sbin/hibernate ]; then
  /usr/local/sbin/hibernate $HIBERNATE_ARGS ;
#  exit $?;
  exit;
fi

# . /usr/share/acpi-support/power-funcs
# . /usr/share/acpi-support/policy-funcs

if [ x$ACPI_HIBERNATE != xtrue ] && [ x$1 != xforce ]; then
  exit;
fi

# Unset video posting - it's not needed for suspend to disk
unset POST_VIDEO
unset USE_DPMS

. /etc/acpi/prepare.sh

#if [ x$LOCK_SCREEN = xtrue ]; then
#    for x in /tmp/.X11-unix/*; do
#	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
#	getXuser;
#	if [ x"$XAUTHORITY" != x"" ]; then
#	    export DISPLAY=":$displaynum"
#	    . /usr/share/acpi-support/screenblank
#	fi
#    done
#fi

echo -n $HIBERNATE_MODE >/sys/power/disk

if [ -x /sbin/s2disk ]; then
    DEVICE="/dev/disk/by-uuid/`awk -F= '{print $3}' </etc/initramfs-tools/conf.d/resume`"
    if [ -f /etc/usplash.conf ]; then
	. /etc/usplash.conf
	/sbin/s2disk -x "$xres" -y "$yres" $DEVICE
    else
	/sbin/s2disk $DEVICE
    fi
else
    echo -n "disk" >/sys/power/state
fi

$LAPTOP_MODE stop

. /etc/acpi/resume.sh
```

/etc/acpi/events/ibm-sleepbtn
```
# /etc/acpi/events/ibmsleepbtn
# Called when the user presses the sleep button

event=ibm/hotkey HKEY 00000080 00001004

#action=/etc/acpi/sleep.sh
action=/etc/acpi/sleepbtn.sh
```

/etc/default/acpi-support
```
# Comment the next line to disable ACPI suspend to RAM
# ACPI_SLEEP=true

HIBERNATE_SCRIPT=true
HIBERNATE_ARGS=
# HIBERNATE_SCRIPT_RAM=true
# HIBERNATE_RAM_ARGS="-F /etc/hibernate/both.conf"

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=mem

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12
```

/etc/hibernate/suspend2.conf
```
# Example suspend2.conf file.
# 
# See hibernate.conf(5) for help on the configuration items.
#
# NOTE: Suspend2 is an improved version of suspend-to-disk which currently
#       requires patching your kernel. For more information, see www.suspend2.net
# 
#       If you do not wish to patch your kernel but still be able to suspend to
#       disk, see disk.conf instead.

### suspend2 (for Software Suspend 2)
UseSuspend2 yes
Reboot no
EnableEscape yes
DefaultConsoleLevel 1
Compressor lzf
Encryptor none
# ImageSizeLimit 200

## useful for initrd usage:
# SuspendDevice swap:/dev/hda2

## Powerdown method - 3 for suspend-to-RAM, 4 for ACPI S4 sleep, 5 for poweroff
# PowerdownMethod 5

## Any other /proc/software_suspend setting can be set like so:
# ProcSetting expected_compression 50

## Or traditionally like this:
# Suspend2AllSettings 0 0 2056 65535 5

## Or even from the results of hibernate --save-settings with this:
# Suspend2AllSettingsFile /etc/hibernate/suspend-settings.conf

## For filewriter:
# FilewriterLocation /suspend_file 1000
# VerifyFilewriterResume2 yes

## Specify a userui like this:
# ProcSetting userui_program /usr/local/sbin/suspend2ui_text
# ProcSetting userui_program /usr/lib/suspend2-userui/suspend2ui_text

# Scale CPU to full speed to make sure we suspend as fast as possible.
FullSpeedCPU yes

Include common.conf
```

Any ideas? Thanks in advance

---

