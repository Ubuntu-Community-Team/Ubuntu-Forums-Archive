---
title: "Disable sleep/standby/display sleep"
date: 2008-05-18
forum: Hardware
---

### Post by jlongstreet on 2008-05-18
I have an HTPC with a Gigabyte GA-MA78GM-S2H board and Athlon 64.  I have it connected via HDMI to my TV, and only control it using a remote.  However, after about 15 minutes, some sleep mode is activated, and the HDMI signal cuts out until I wiggle/click the mouse.

I have the screensaver disabled in the Screensaver page of the Settings Manager, so it's not that.

My /etc/default/acpi-support reads:
```

# Comment the next line to disable ACPI suspend to RAM
#ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true

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
#USE_DPMS=true

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
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

```

Since commenting out the ACPI_SLEEP, ACPI_HIBERNATE, and USE_DPMS lines, I've restarted acpid and acpi-support, with no effect.

I'd rather not turn power management off entirely (I still want the ability to turn the machine off and all that), but I don't want to have it going to sleep after 15 minutes.

---

### Post by bobblehat on 2008-05-18
How about System->Preferences->Power Management then change the time before the display sleeps?

---

### Post by jlongstreet on 2008-05-18
I installed gnome-power-manager (I assume that's where System->Preferences->Power Management comes from) and ran gnome-power-preferences.  Both display sleep and system sleep are set to Never.

I'm testing with the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=787600&highlight=suspend](http://ubuntuforums.org/showthread.php?t=787600&highlight=suspend)

I also put an early-out exit; in /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux, power-suspend-hybrid-linux, power-hibernate-linux, and power-set-power-save-linux, as well as /etc/acpi/sleep.sh.

Hopefully this will work.

---

