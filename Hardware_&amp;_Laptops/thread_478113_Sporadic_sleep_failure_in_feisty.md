---
title: "Sporadic sleep failure in feisty"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by bcw on 2007-06-19
Hello,

Sleep and hibernate generally work, but ocassionally, sleep locks the machine before sleeping.  The screen is black, but backlight glow shows around the edges of the black pixels.  The power and battery/charge lights are on, and there is no response from the machine - I must force a power-off and reboot.  The computer appears to be running, but unresponsive.

Running '/etc/acpi/sleep.sh force' manually causes this everytime (I've tried it), but it only happens ocassionally if I select the 'Sleep' button from the shutdown menu.  Sometimes the display does not blank out.

Hibernate appears reliable.

Feisty KDE (not the full Kubuntu install), no upgrades.

Fujitsu Stylistic ST5032D tablet, Centrino-M, 2G RAM.

Does anyone have experience with such?

Cheers,
Bret

My /etc/default/acpi-support file:
```
# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

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
SAVE_VIDEO_PCI_STATE=true

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
###LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```

---

