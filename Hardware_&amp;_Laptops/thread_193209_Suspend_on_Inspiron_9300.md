---
title: "Suspend on Inspiron 9300"
date: 2006-06-09
forum: Hardware &amp; Laptops
---

### Post by crawfjs on 2006-06-09
My 9300 suspends to disk just fine, but when I do the "suspend to memory" (or sleep), it never wakes.  The processor light is on, but my optical mouse (USB), keyboard and screen never wake.  Any help would be greatly appreciated.  (I'm actually using 5.10 Breezy Badger)

---

### Post by pantropik on 2006-06-09
What video card do you have -- the nVidia 6800 Go or the ATI X300?  I have the 6800 with the nVidia drivers installed and it sleeps fine.  Before I installed the proprietary drivers (using Automatix) sleep would fail.

---

### Post by crawfjs on 2006-06-10
Ya, I have the X300.

---

### Post by barakaspeed on 2006-06-12
I have the 9300 with Nvidia Geforce 6800 and can't even get it to work either.  pantropik, there was nothing else that you did besides installing the drivers via automatix?  What Driver version of Nvidia are you using?

crawfjs, just for kicks, when you come out of sleep and it appears everything is not waking,  Hit  <Control><Alt> + F7.  I notice when I do that, it does show my mouse pointer on a black background.  I know it's not a fix, but maybe a troubleshooting step that might help us if it does the same for you.

I have tried these two wiki's, but it never helped.

[https://wiki.ubuntu.com/SuspendHowto?highlight=%28suspend%29](https://wiki.ubuntu.com/SuspendHowto?highlight=%28suspend%29)
[https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend?highlight=%28suspend%29](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend?highlight=%28suspend%29)

---

### Post by emperor on 2006-06-13
[quote=crawfjs]My 9300 suspends to disk just fine, but when I do the "suspend to memory" (or sleep), it never wakes.  The processor light is on, but my optical mouse (USB), keyboard and screen never wake.  Any help would be greatly appreciated.  (I'm actually using 5.10 Breezy Badger)[/quote]

I had the same problem with Breezy. Suspend works on my i9300 with Dapper but it took some tweaks to "/etc/default/acpi-support". However, hibernation does not work. I have the ATI video and the fglrx running with 3D support.

---

### Post by boom2k1 on 2006-06-13
What specific tweaks did you use to make it work?

---

### Post by emperor on 2006-06-13
Before I made the final tweaks to the "/etc/acpi-support" file, the screen would lock-up when returning from sleeping about once a day. There were usually some large vertical gray and black bars frozen on the screen. After the final tweaks I now see smaller gray and black horizonal bars sometimes, but it never locks up. On occassion, I find that I have to login as though the screen is locked or I am logging in from a remote terminal. 

I will post my '/etc/default/acpi-support" file this evening as my laptop is at home. 


There were two other changes that were made to gdm.conf and xorg.conf in an effort to correct the logout crash or lockup in general.

****
Changed the option in     /etc/gdm/gdm.conf
 
AlwaysRestartServer=true


  *****

I also set "UseInternalAGPGART" to "no" in xorg.conf

Section "Device"
 Identifier  "aticonfig-Device[0]"
 Driver      "fglrx"
        Option      "UseInternalAGPGART" "no"
EndSection

*****

---

### Post by emperor on 2006-06-13
Here's my acpi-support file:
===================

# Uncomment the next line to enable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
#ACPI_HIBERNATE=true

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
POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
#HIBERNATE_MODE=shutdown

---

### Post by emperor on 2006-06-19
Update on Dell i9300:

One side-effect of suspend when using ATI's fglrx driver is that sometimes my wireless mouse quits working (completely or just the scroll feature) when I wake up the machine. I also find that the extra terminal sessions via CTL-Alt F2/F3/... quit working sometimes. So, as a result of these side effects, I have switched to the "ati" video driver. I now find both suspend and hypernate work initially but will not know how well for a few weeks of testing. I will report back any problems or long term success.

---

