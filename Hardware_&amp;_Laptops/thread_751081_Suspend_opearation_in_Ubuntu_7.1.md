---
title: "Suspend opearation in Ubuntu 7.1"
date: 2008-04-10
forum: Hardware &amp; Laptops
---

### Post by adg on 2008-04-10
HI,

I am new to ubuntu 7.1 and using it on Thinkpad R61. 

I am trying this suspend functinality. I edited /boot/grub/menu.lst and added acpi_sleep=s3_mode .
It works when I press suspend, it is suspended. When I press power button, it resumes. If I do this 3-4 times after that only blank screen appears and I need to restart the laptop. 
Also I have made "Do Nothing" setting in Power Management 'When laptop lid is closed' setting.

Please help me on this I need to restart the laptop 6-7 times a day due to this error.

This is my /etc/default/acpi -support file:

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
MODULES="iwl4965 iwlwifi_mac80211 cfg80211"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
#SAVE_VBE_STATE=true
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true
POST_VIDEO=false

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
#HIBERNATE_MODE=shutdown
HIBERNATE_MODE=platform

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

---

### Post by adg on 2008-04-12
Any inputs??

---

### Post by srt4play on 2008-04-27
Do you have intel or nvidia graphics?  I have a R61 with intel 965GM graphics and I get a black screen on resume from suspend. I can do ctrl-alt-F1 then ctrl-alt-F7 to get it back without restarting.

---

