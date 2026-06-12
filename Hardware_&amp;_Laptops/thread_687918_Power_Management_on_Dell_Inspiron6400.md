---
title: "Power Management on Dell Inspiron6400"
date: 2008-02-04
forum: Hardware &amp; Laptops
---

### Post by Tripero on 2008-02-04
Hi guys... I've been searching the web and this forum for answers regarding this subject with no success at all, that's why I really hope anyone can give me a hand here...

The problem is, I can't make the lid close event and the idle event work properly, running on ac power; the first, causes no action and the last always seems to trigger the "blanck screen" action, despite I tried many times changing the configuration using 'gnome-power-preferences'.

Any ideas? I found many posts regarding acpi problems, and tried unseccessfully many changes (that I don't even remember) in /etc/default/acpi-support. I'm copying the contents of it below.
I running Ubuntu Gutsy 64b, on a Dell Inspiron 6400 (Core2Duo1.73, Ati X1400).

Thanks in advance, 
   Dario


[FONT="Courier New"]----------------
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
ENABLE_LAPTOP_MODE=true

# Spindown time on battery
SPINDOWN_TIME=12
-----------------------[/FONT]

---

