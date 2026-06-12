---
title: "Help with HP DV5Z Suspend/Resume Ubuntu 8.10"
date: 2008-12-10
forum: Hardware
---

### Post by Berndawg3 on 2008-12-10
Hey everyone,

I just got a new laptop, HP DV5Z, and I decided to get rid of windows and learn Ubuntu on it.  I'm running Ubuntu 8.10 64-bit.  Most things have been working well on it, but suspend/resume are not working.  It's odd because hibernate works fine, but not suspend/resume.  The  machine suspends fine, but upon resume the screen just stays black.  The HDD light and keyboard lights come back on so I know it's making a start, but I wish there was some way to totally unload and reload my video device, if that's even possible.  For what it's worth, I'm using ATI HD3200 integrated graphics. 

I'll post my ACPI-Support and Xorg.conf files:

#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

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
# USE_DPMS=true

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
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=false

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 







Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option "VBERestore" "true"
EndSection



I'm still a bit of a Linux noob, but I have a basic understanding of the terminal and things, so I would appreciate any and all help!

Thanks,
Andy

---

### Post by Berndawg3 on 2008-12-10
Can anybody help me?

---

### Post by Berndawg3 on 2008-12-11
...anyone?

---

### Post by motang on 2008-12-11
I might not be of much help, but for me I noticed that when I don't have the video drivers installed (just use the default one which in turn I can't use compiz-fusion) my hibernate works as it suppose to, but when I have it installed my hibernate doesn't work but suspend some what works. I say somewhat because, if I have too much apps open, when I resume the hard drive is used extensively and I can't use the computer at all and I have to hard shut down, but if have very little apps open (one or two) my suspend works great.

My question to you is, do you have the video drivers installed?  You check this by going to *System -> Administration -> Hardware Drivers*.

---

### Post by Berndawg3 on 2008-12-11
Thank you motang.  Yes, I do have the ATI FGLRX drivers installed and I'm running Compiz Fusion.

---

### Post by motang on 2008-12-11
You are welcome, and looks like we are in the same boat.  I do admit that suspend has come a long way (before it didn't work at all) and it has to do more with ATi and not Ubuntu or Linux in general.  Hope fully this will be fixed soon. :)

---

### Post by Berndawg3 on 2008-12-11
It's funny because I was working on this suspend issue before using the following guide:  [http://www.linlap.com/wiki/getting+suspend+and+hibernate+working+in+ubuntu+7.10](http://www.linlap.com/wiki/getting+suspend+and+hibernate+working+in+ubuntu+7.10)

This guide did not work for me, but I continued messing around with the ACPI-support file.  Now, I don't remember my exact settings, but I remember changing the RADEON_LIGHT to true, and then suspend worked!  But only for a day, since I tried it again the next day and it quit working.  I can't figure out if I changed something in that time that messed something up.  I jhave no idea what really happened.

---

### Post by Berndawg3 on 2008-12-11
Holy ****!  I just edited my ACPI-support file a bit more and it suspended successfully!  I'll post my acpi-support text again, and I'll keep you updated on whether or not it keeps working

```
#
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

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
# USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
RADEON_LIGHT=true

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
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=true

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 
```

---

### Post by motang on 2008-12-11
Awesome, so it works flawlessly?  I am going to try it out over the weekend as my notebook is what I use for my school work and I have my last finaly tomorrow (presentation on independent study) and I have all my work (my very own blogging software) on it and don't want to mess it up.  Thanks man.

---

### Post by Berndawg3 on 2008-12-11
Yeah, I know how you feel about school work.  I have all of my finals next week, so I'll be using this notebook pretty heavily as well.  Good luck on all of it.

---

### Post by Berndawg3 on 2008-12-11
Yeah, I know how you feel about school work.  I have all of my finals next week, so I'll be using this notebook pretty heavily as well.  Good luck on all of it.

---

### Post by motang on 2008-12-11
> **Berndawg3 said:**
> Yeah, I know how you feel about school work.  I have all of my finals next week, so I'll be using this notebook pretty heavily as well.  Good luck on all of it.
Thanks, good luck to you as well! :D

---

### Post by motang on 2008-12-15
Well I changed mine a little bit and it worked out beautfully, I had many programs open and it was able to come back from suspend very quickly...exactly the different from before.  Thanks man.  I have to posted my *acpi-support* file.

```
#
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

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
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=true

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 
```

---

### Post by mozychan on 2008-12-16
Hey,

I just got this notebook as an early Christmas gift and I'm experiencing the same problem, only I have a 256MB ATI Radeon(TM) HD 3450 Graphics instead.  I tried making the changes in the acpi-support file only to find no improvement.  Any further advice would be much appreciated.

---

### Post by motang on 2008-12-28
Just updated to 64bit and it seems that suspend doesn't work at all, the screen is black so I swiched back to 32bit.

---

### Post by fredknex on 2009-01-01
On a clean 8.10 install with my dv5z it seems that its the mouse and keyboard that are not resuming. my external usb mouse did however resume, and clicking while at the usually blank screen after resuming from suspend brings up the login box...unfortunately i have no usb keyboard to log back in and see what else is working/not working.

---

### Post by mozychan on 2009-01-23
> **motang said:**
> Just updated to 64bit and it seems that suspend doesn't work at all, the screen is black so I swiched back to 32bit.

ahhh, that would be my problem.  figures.  thanks, but I'm never going back to 32, bwahahahaha!

-moose

---

### Post by motang on 2009-01-24
LOL, I know what you mean that's the way I am with my desktop.

---

### Post by mozychan on 2009-02-15
I don't know what I did, but the situation has changed a bit.  Now I can resume, but once revived the keys and mouse are frozen.

Also, whenever I try to lock the screen the video tears really bad when I try to unlock.

The cause may have been my installing Catalyst 9.1 or a number of other updates that have occured since my last use of these features (which was around the time of my last post).

Still running 64...

For now I've just disabled the auto suspend and screen lock functions until I can figure things out.

-moose

---

### Post by motang on 2009-02-16
I can only suspend and hibernate once per boot.  Any more it won't work, I also have Catalyst 9.1 installed and I do like that it's snappy with compiz, and I am still on 32bit, I just hope by 9.04 it would be fixed I mean it's 2009 and this kind of stuff should work flawlessly.

---

### Post by motang on 2009-02-26
Here is my updated acpi-support:

> #
# Configuration file for the acpi-support package
#
#
# The acpi-support package is intended as "glue" to make special functions of
# laptops work. Specifically, it translates special function keys for some
# laptop models into actions or generic function key presses.
#


#
# Suspend/hibernate method
# ------------------------
#
# When gnome-power-manager or klaptopdaemon are running, acpi-support will
# translate the suspend and hibernate keys of laptops into special "suspend"
# and "hibernate" keys that these daemons handle.
#
# Only in situations where there is no gnome-power-manager or klaptopdaemon
# running, acpi-support needs to perform suspend/hibernate in some other way.
# There are several options for this. The options are:
#
# dbus-pm:
#    Perform suspend and hibernate actions via a DBUS request to the power
#    management daemon. This works for power management daemons that we don't
#    know of. (For gnome-power-manager and klaptopdaemon this will do nothing,
#    since those will be detected when they are running, and triggered using
#    a virtual keypress.)
#
# dbus-hal:
#    Perform suspend and hibernate actions via a DBUS request directly to HAL,
#    bypassing any running power management daemons.
#
# pm-utils:
#    Use pm-suspend and pm-hibernate to suspend and hibernate. (The dbus method
#    normally results in this as well, but calls through dbus. Use this option
#    only if you don't have dbus installed.)
#
# hibernate:
#    Use the hibernate package to suspend and hibernate.
#
# acpi-support:
#    Use the legacy built-in suspend/hibernate support. (DEPRECATED)
# 
# none:
#    Do not attempt to suspend/hibernate. Set SUSPEND_METHODS="none" to
#    disable suspend/hibernate handling in acpi-support.
#
# If you specify dbus or pm-utils, the result will normally be the same as when
# you suspend from your desktop environment. If you specify "hibernate" or
# "acpi-support", be aware that this probably does not match what your desktop
# environment would do (unless you have managed to configure something so that
# the DBUS power management interfaces call the hibernate package).
#
#
# Please specify a space separated list of options. The recommended value is
# "dbus pm-utils"
#
SUSPEND_METHODS="dbus-pm dbus-hal pm-utils"



#
# LEGACY BUILT IN SUSPEND SUPPORT (DEPRECATED)
# --------------------------------------------
#
# These options only work for the "acpi-support" suspend method. This is NOT
# recommended, but is retained for backward compatibility reasons.
#

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=false

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
SAVE_VIDEO_PCI_STATE=false

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
# hangs on some machines.  (Note: This is reported to cause breakage in
# Debian - see deb bug #425800.  Leaving enabled for Ubuntu for now
# since presumably it's still valid here.)
ENABLE_LAPTOP_MODE=true

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf.

Now it works like it suppose to. I can have a lot of programs running at the sametime and it wakes up from suspend in like 30 seconds, sometimes it might a little bit longer but it ascutally works.  I hope this helps out.

---

### Post by mozychan on 2009-03-25
> **motang said:**
> 
Now it works like it suppose to. I can have a lot of programs running at the sametime and it wakes up from suspend in like 30 seconds, sometimes it might a little bit longer but it ascutally works.  I hope this helps out.

Is this with 64-bit?  I'll see if it helps me at all when I have time.  Recently I tried getting it to work and I've discovered a cruel method that does the job.

When I suspend the computer, the keyboard and mouse lock up leaving only the power button usable to resume the computer from sleep.  Normally on this laptop, once the system and display have resumed, the keyboard and mouse remain locked.  The way to get around this is by punching any key or keys repeatedly right after pushing the power button and during the resuming process.  It seems to work every time, but it's a nuisance.

If I so happen to forget to punch the keys on resume then all I need to do is close the lid and let it fall asleep again.  Then try again.

Another annoyance is that suspend and resume also drops my usb linksys wireless adapter every time so I have to re-plug it in to get it re-recognised.

-moose

---

### Post by motang on 2009-03-25
Nope 32 bit, I have no luck at all in 64 bit.

---

