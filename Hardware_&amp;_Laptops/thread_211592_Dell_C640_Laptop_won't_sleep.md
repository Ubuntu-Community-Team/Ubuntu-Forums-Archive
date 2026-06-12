---
title: "Dell C640 Laptop won't sleep"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by ddumanis on 2006-07-08
Anyone else have any luck getting this machine to suspend?

I've tried messing around with /etc/default/acpi-support settings, but nothing seems to work. The error I get when I try to put it to sleep:

"Two processes failed to stop..." 

Then it wakes back up!

Thanks for any and all advice.

---

### Post by ddumanis on 2006-07-09
OK, for anybody else who owns this computer, here's what finally worked. (This is for sleep only--I don't know about hibernation.)

Set /etc/default/acpi-support to read like this:


# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

# Change the following to "standby" to use ACPI S1 sleep, rather than S3.
# This will save less power, but may work on more machines
ACPI_SLEEP_MODE=standby

# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
# POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
DISABLE_DMA=true

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

---

### Post by chasisaac on 2006-07-13
Uhm, thank you!

---

### Post by Erik Andrén on 2008-02-23
This is resolved with this commit to the ati driver:
[http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=commit;h=a0a73208a21546ac120fb9a463261836c9ea7b55](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=commit;h=a0a73208a21546ac120fb9a463261836c9ea7b55)

See also:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-ati/+bug/34155](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-driver-ati/+bug/34155)

---

