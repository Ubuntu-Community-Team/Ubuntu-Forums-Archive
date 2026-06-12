---
title: "HELP! Blank screen after suspend w/ both VESA &amp; FGLRX"
date: 2008-01-29
forum: Hardware &amp; Laptops
---

### Post by fictivetoast on 2008-01-29
I recently had to wipe my laptop and reinstall Gutsy.  Previously, I had no trouble suspending/resuming with either the default VESA or the ATI 7.12 display drivers.

BUT now, after reinstalling, I can't get the computer to wakeup from a suspend with either the VESA driver or the new 8.01 ATI driver.  No clue what's different this time around, but apparently something must be.  The laptop appears to go to sleep just fine, but when it wakes I'm stuck with a blank screen : ctr+alt+backspace doesn't respond, nor does an attempt to switch to the terminal.  Occasionally I'm able to get the thing to cold reboot using alt+printscreen+REISUB, but not always.

I've already tried changing acpi-support's POST_VIDEO and SAVE_VBE_STATE to false, but to no avail.  Please help if you have any suggestions!!!  Since I can't resume on VESA either, I don't think it's just a driver issue.

Here's the contents of my /etc/default/acpi-support : 
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
MODULES_WHITELIST="fglrx"

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

---

### Post by fictivetoast on 2008-01-29
Hmm, oddly have gotten things to work by reverting to the 7.12 ATI drivers I had backed up.  Very weird.

Oh well, I spose I'll stick with the interim old drivers until the next iteration.

---

### Post by coskierken on 2008-02-01
Here is the link for the fix for ATI 8.01.  

[http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23](http://www.phoronix.com/forums/showpost.php?p=23097&postcount=23)

Here is a link for a Compiz Switch to easly go back to no special effects to have good video playback.  

[http://forlong.blogage.de/article/pages/Compiz-Switch](http://forlong.blogage.de/article/pages/Compiz-Switch)

Hope this helps.  Oh, if you have xserver-xgl installed with the latest ATI 8,01 release, purge it from the system.  It is not longer needed for Compiz-Fusion.  It was built with AEGLX in the code.  They have made at least one step forward.  The effects are smoother and just plain work better.

---

