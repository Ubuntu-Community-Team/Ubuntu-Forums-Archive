---
title: "ibm x30 and xubuntu"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by frenzis on 2007-11-24
Hi everyone!

Just moved to xubuntu from linuxmint 2 barbara. The tests from the cd were fine so I installed.
Once installed the wireless and usb were not working...I tried many things..but nothing worked....after a while everything showed up...and works fine.

I still have a question and a problem

1) in my network I see 2 wireless, the wlan0 and wifi0....I don't want to mess up things as it works fine, but why do I have 2? While on the live CD I just had eth1...

2) I cannot close my laptop or leave it in idle to the screen saver or in sleep mode as it will not come back (actually sometime the mouse comes back...but the rest stays black)...do you have a fix for this?

Thanks all for your time and help.

Frenzis.

---

### Post by frenzis on 2007-11-28
FYI:

I more or less solved the sleep issue (n2)..now I get my screen back 4 out of 5 times.

I just modified the acpi-support file like this:


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
# SAVE_VIDEO_PCI_STATE=false

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
LOCK_SCREEN=false

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=false

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


Still have the other issue.

Frenzis.

---

### Post by TheFuzzball on 2007-11-28
Sounds a lot like my problem that I would also like a fix to, I use Kubuntu Gutsy and when I leave my laptop (Thinkpad X30) screen closed for a short period of time and then open it again I can't come back and the screen stays black (not even mouse), It's always fine when I reboot but its a real pain.

---

### Post by frenzis on 2007-11-29
try the same thing I did, but make a back up of the file before..just in case ;)

Let me know

Frenzis.

---

### Post by orawax on 2008-01-08
> **frenzis said:**
> 2) I cannot close my laptop or leave it in idle to the screen saver or in sleep mode as it will not come back (actually sometime the mouse comes back...but the rest stays black)...do you have a fix for this?

I found this: 
[http://ubuntuforums.org/showthread.php?t=52067&highlight=ibm+thinkpad+x30](http://ubuntuforums.org/showthread.php?t=52067&highlight=ibm+thinkpad+x30)

In xorg.conf change the display driver from 'intel' to 'i810' and add some options. Seems to work 100% (so far).

Now if anyone has had trouble with getting sound out of X30 and has a solution, I'd appreciate...

---

