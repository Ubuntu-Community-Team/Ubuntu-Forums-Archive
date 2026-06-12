---
title: "Closing lid on an Inspiron 5100 does nothing"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by NeoChaosX on 2005-11-08
Topic pretty much says it. Nothing happens when I close my Dell Inspiron 5100 with Ubuntu, not even a screen-blanking to save power. Any other 5100 owners with this problem and/or managed to get it working?

---

### Post by Davor281 on 2005-11-10
Hi!

Could you post :

/etc/acpi/events/lidbtn

and

/etc/default/acpi-support

ENjoY!

Davor.

---

### Post by NeoChaosX on 2005-11-12
/etc/acpi/events/lidbtn:
```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```

/etc/default/acpi-support:
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
ENABLE_LAPTOP_MODE=false
```

---

### Post by Davor281 on 2005-11-13
I don't have a Radeon laptop, so I am not sure, but try to change the /etc/default/acpi-support line -

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

to

# Use Radeontool to switch the screen off? Seems to be needed on some machines
RADEON_LIGHT=true


ENjoY!

Davor

---

### Post by NeoChaosX on 2005-11-13
That requires the radeontool package to be installed, and given it's description in Synaptic, I don't want to take a risk of damaging my hardware installing it. :?

---

### Post by NeoChaosX on 2005-11-15
Okay, so I got it working. I did what you suggested, Davor, but I also modified my GRUB menu.lst file to look like this (change bolded):

```
title		Ubuntu, kernel 2.6.12-9-686 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hdc5 **acpi_irq_balance** ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot
```

I got the tip from [this page](http://cabibbo.physics.wm.edu/~bryan/computer/inspiron5100.html) (look for the section about not recieveing events from acpid). WHen I rebooted with that option in menu.lst, the laptop began shutting off the screen when I closed the lid.

---

### Post by tompicking on 2006-06-03
I just added the acpi_irq_balance parameter in menu.lst. Works a treat! Thanks

---

