---
title: "IBM Thinkpad X32 suspend / resume problem"
date: 2014-10-25
forum: Hardware
---

### Post by flefle on 2014-10-25
Hi, 
on a IBM Thinkpad X32 with Xubuntu 14.04,

I would like to have some hints on how to debug my suspend / resume problem 

The computer seems to suspend / resume correctly (very fast, very promising) except for the fact that the screen is scrambled upon resume. 
However I think the system is working as I can type (blindly) the reboot order in a terminal; 
Also, weird enough, if I do an hibernate after the suspend / resume sequence, then the display is correctly restored !
(except that sometime I get into the blinking cursor and kernel panic problem)

For suspend / resume I invoque pm-suspend directly.
I had a look at log file /var/log/pm-suspend.log and set the PM_DEBUG flag but I cannot see anything wrong in the file
I also had a look at the X11 log, but what to look for ?
I also had a look at dmesg, but everything seems ok
I see that there is a "quirks" script devoted to the X32, and my hardware is recognized, but at the end, it does not work
I tried to tweek the scripts by puting a script in /etc/pm/config.d/, but I'm not sure what command get really executed

Ultimately, the question is : has it every worked  ?
when I was using 12.04 it didn't

Thank you for your help

---

### Post by tgalati4 on 2014-10-25
What graphics chip are you using?

```
lspci | grep VGA
```

How much RAM do you have?

```
free
```

There are several settings in /etc/default/acpi-support.  Review them:

```
cat /etc/default/acpi-support
```

You will have to get very familiar with your hardware to solve this problem.  [http://www.thinkwiki.org/wiki/Category:X32](http://www.thinkwiki.org/wiki/Category:X32)

Your graphics chip is probably:  [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7000)

Thinkpads generally work well in linux and since this laptop has been around for a while (2005 vintage), newer kernels (newer distros) will probably not fix a configuration problem that existed in 12.04.

---

### Post by flefle on 2014-10-25
hi, thank you for helping

```
lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV100/M6 [Rage/Radeon Mobility Series]

```

```
fle@fle-X32:~$ free
             total       used       free     shared    buffers     cached
Mem:       1025392     600052     425340       6956      24000     199892
-/+ buffers/cache:     376160     649232
Swap:      1951740      83740    1868000

```

```
fle@fle-X32:~$ cat /etc/default/acpi-support
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
POST_VIDEO=true

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

# Add to this list network interfaces that you don't want to be stopped
# during suspend (in fact any network interface whose name starts with
# a prefix given in this list is skipped)
SKIP_INTERFACES="dummy qemu"

# Note: to enable "laptop mode" (to spin down your hard drive for longer
# periods of time), install the laptop-mode-tools package and configure
# it in /etc/laptop-mode/laptop-mode.conf. 

```

I tried to use this file, with the intention of dropping any parameter and trying to find he good ones. Isn't it conflicting with the acpi-support file ? also the options in the file look very much like the --quirk-* scripts, is it the same thing ?

```
fle@fle-X32:~$ cd /etc/pm/config.d/
fle@fle-X32:/etc/pm/config.d$ ls
97ATI_RADEON  thinkpad_acpi
fle@fle-X32:/etc/pm/config.d$ cat 97ATI_RADEON
PM_DEBUG="true"
# DROP_PARAMETERS = "--quirk-s3-bios  --quirk-s3-mode --quirk-dpms-suspend"
DROP_PARAMETERS = "all"
echo "ATI RADEON QUIRK ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~"fl

```

---

### Post by flefle on 2014-10-25
ok, I am playing at random with pm-suspend options :

--quirk-vga-mode-3 --quirk-radeon-off  -> OK
--quirk-vbe-post --quirk-radeon-off      -> FAIL
--quirk-vbemode-restore --quirk-radeon-off   -> FAIL (in fact works, but the screen is black because it is not redrawn, doing CTRL-ALT-F1 then CTRL-ALT-F7 and it is all there) 
--quirk-vbestate-restore --quirk-radeon-off     -> FAIL (i can see some display corruption at the top of the screen)
--quirk-save-pci --quirk-radeon-off  -> OK

I don't have any explanation as to why some work and not the other. I'm a total noob regarding linux, I just know the man command.

so now lets see how to make these things permanent :
I created a file sudo leafpad /etc/pm/config.d/99_ATI_RADEON, with the following content :
```


HOOK_BLACKLIST="98video-quirk-db-handler 99video"

ADD_PARAMETERs="--quirk-radeon-off --quirk-save-pci"


```

this prevents the execution of the hooks provided with pm-utils (the quirks), and it sets my own quirks. 
And this seems to work !

If I don't come back within a few days, one could consider it a success.

---

### Post by flefle on 2014-11-11
After some time, I noticed that the power consumption in suspend mode was too high. Within a couple of hours, the battery would be drained. It took me a lot of effort to fix it, but I think I nailed it.

So as a summary, these are my settings : 

0- install xubuntu 14.04

1- etc/default/grub settings : 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=radeonfb:force_sleep"
then update-grub

2- use of radeonfb :
as here [http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep](http://www.thinkwiki.org/wiki/Problem_with_high_power_drain_in_ACPI_sleep)
> **Ubuntu**

 I used the instructions given by [this site]("http://benbloggt.blogage.de/entries/2008/7/28/Framebuffer-in-Ubuntu-aktivieren") to enable radeonfb in Kubuntu 9.4: 
 
[LIST]
[*] edit /etc/initramfs-tools/modules and add the line "radeonfb" 
[*] sudo update-initramfs -u 
[*] edit /etc/modprobe.d/blacklist-framebuffer and comment out the line "blacklist radeonfb" 
[/LIST]



3- then create the /etc/pm/config.d/99_ATI_RADEON file, as said previously with the following :
DROP_PARAMETERS=all
ADD_PARAMETERs="--quirk-radeon-off --quirk-save-pci"

4- install radeontool via the software center

I think that's all, 
as above, if I don't post within a few days, you can consider that it works for me.

---

