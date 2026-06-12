---
title: "No ACPI or Suspend on Shuttle X200"
date: 2009-05-08
forum: Hardware
---

### Post by gbugher on 2009-05-08
I have a Shuttle X200 SFF media-center PC that I'm trying to switch over from Windows to Linux (Ubuntu 9.04 x86.)  This PC, while a "desktop", is based on laptop hardware (laptop optical drive, PC Card-based expansion, miniPCI networking, mobile CPU.)  So far, I've successfully gotten digital sound, HTDV video (Intel GMA 945, 1920x1080), XBMC, MythTV, and the remote control to work, which leaves only one thing -- power management.

On Windows, I can use the remote control to put the system to sleep and to wake it back up.  It's an ACPI BIOS (latest version available for this machine), and all the power management in Windows is ACPI-based. However, in Linux I have not been able to get any ACPI or power management features to work at all.

It at first looks like ACPI is fine.  Contents of some ACPI info files:

/proc/acpi/info:
version:                 20080926

/proc/acpi/sleep:
S0 S1 S4 S5 

acpi -V:
     Thermal 0: ok, 40.0 degrees C
     Cooling 0: Processor 0 of 3
     Cooling 1: Processor 0 of 3
     Cooling 2: Fan 1 of 1

dmidecode and acpidump:
  Attached to this message since they're quite long.

The /proc/acpi directory contains valid, information-filled directories for button, fan, processor, and video -- ACPI is defintiely hooked up.

However, the GNOME power management applet offers only Hibernate and Shutdown options, despite sleep being enabled in the GNOME advanced settings.  Attempts to put the system to sleep fail:

sudo echo ram > /sys/power/state
   Permission denied, even with sudo.

acpitool -s
    Nothing happens at all

Hibernate from the user menu at the top-right:
    Video becomes garbled and machine locks up hard

sudo /etc/acpi/sleep.sh force
Ignoring unknown interface eth0=eth0.
 * Shutting down ALSA...                                                 [ OK ] 
./sleep.sh: line 49: echo: write error: No such device
ifup: interface lo already configured
Ignoring unknown interface eth0=eth0.
 * Setting up ALSA...                                                    [ OK ] 
FATAL: Module button not found.
FATAL: Module button not found.
FATAL: Module fan not found.
FATAL: Module thermal not found.
FATAL: Module fan not found.
FATAL: Module thermal not found.
/etc/acpi/resume.d/72-acpi-pain.sh: line 22: echo: write error: No such device
/etc/acpi/resume.d/72-acpi-pain.sh: line 23: echo: write error: No such device
FATAL: Module acpi_sbs not found.
FATAL: Module ac not found.
FATAL: Module ac not found.
FATAL: Module battery not found.
FATAL: Module battery not found.
FATAL: Module acpi_sbs not found.

All of the "write error: No such device" lines are in response to attempts to write /sys/power/state, which does exist on the system.  Obviously, only the first two lines are from the attempt to sleep, while the other lines seem to be attempting to "resume" a system that never shut down.

I've tried following various ACPI HOWTOs on the net, but haven't found anything at all helpful for my problem.  For one, lsmod doesn't list any of the common ACPI modules (button, fan, etc.), but they still show in /proc/acpi, so I presume they're just compiled directly into the kernel in Jaunty.  They all seem to be about how to resolve issues with machines not waking up properly -- not machines refusing to even attempt to sleep!

Any ideas what I can do to get this to go to sleep?  Am I stuck with building an APM kernel and giving up on ACPI altogether?  (Talking of which, the usual instructions for swapping to APM  -- adding acpi=off and noacpi to the kernel boot line in menu.lst, and adding apm to the /etc/modules file -- didn't seem to work on Jaunty, with all APM applications just throwing up "no APM support in kernel."  Did they rip APM out in 9.04?  I'm assuming a kernel recompile could fix this in any case.)

---

