---
title: "laptop mode"
date: 2005-10-17
forum: Hardware &amp; Laptops
---

### Post by duffman25 on 2005-10-17
Hi

laptop-mode is disables by default, anyone knows how to enable it? I've commented out in my /etc/defaults/acpi-support file the last section like this:
```


# Uncomment the next line to enable ACPI suspend to RAM
#ACPI_SLEEP=true

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
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
# ENABLE_LAPTOP_MODE=false


```

But i'm not sure if this is it. I don't "hear" my centrino accelerating & during breezy development with laptop-mode on by default I could hear the processor accelerating during battery mode.

Thanxs

---

### Post by boles on 2005-10-18
I am not sure, but I think you should leave the last line uncommented and have to change *false* into *true*.

---

### Post by xx404 on 2005-10-18
The previous poster is correct. I simply changed the value from false to true and when running on battery my hard disk now spins down. One problem that I have discovered though is that if you boot on battery it's not smart enough to enable laptop-mode. You'll have to do it manually by typing 

    laptop-mode start 

from a shell as root.

On hoary I replaced the laptop-mode package with the latest version of laptop-mode-tools which was much better but the new acpi-support package seems to interfere with it.

---

