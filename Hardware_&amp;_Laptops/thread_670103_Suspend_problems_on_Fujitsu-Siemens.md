---
title: "Suspend problems on Fujitsu-Siemens"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by spyxter on 2008-01-17
Hi there!

I've got a little problem - can't get my notebook to wake up from suspend properly. I looked through a lot of threads here, but couldn't find the solution.

So the computer goes to suspend mode a-ok. I get my "sleep" indicator flashing as it's supposed to, but when I wake up the pc all I get is a black screen with an underscore cursor flashing in the upper right corner. Crtl + Alt + Delete seems to work fine, pc restarts and runs normally.

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
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=false

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

```

This is how my /etc/default/acpi-support file looks like.

It would awesome to hear some suggestions :)

BTW, my notebook's called Fujitsu-Siemens Amilo Pi-1556.

---

### Post by Sjors on 2008-01-22
I have a Fujitsu Lifebook A1330. Mine crashes completely (black screen, no mouse) on a wake-up after suspend; not even the keyboard responds. Hibernate works, except that I can not connect to my home Wifi on wakeup.

---

