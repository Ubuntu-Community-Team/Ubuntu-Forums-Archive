---
title: "Problems getting suspend to work when closing lid on IBM X31"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by Zyzzyva100 on 2005-11-23
So I finally decided that I needed to install Linux on my laptop, and having heard great things about laptop support with breezy, I figured I would give it a try.  Barring a few small issues, everything is up and running after about 3 hours.

Now let me preface this by saying that I am not a linux newbie, I run gentoo on my desktop.  I just wanted something easier to setup for my laptop, but I will say I've never configured linux on a laptop, nor used a debian based distro (although I can't say thats its terribly hard to adapt).

Anyway, when I close the lid right now, nothing happens.  But fn-f4 seems to suspend to ram, and when I reopen the lid everything comes back right away perfectly.  I just wish I could close the lid and have it do the same thing that fn-f4 does.

So, here are the configs I have changed thus far to try and get what i want working:```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh

```

```
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
SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

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
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```

So I basically just tried to enable suspend to ram, disabled suspend to disk and installed and enabled the radeon_light tool.  Let me note, though, that this has changed nothing vs. the "out of the box" config.  What I have working now is what I had working when I first installed.  I just can't seem to make the lid button actually do anything.

So, anybody have any ideas?

---

### Post by timetunnel on 2005-11-23
For me (IBM R52) it was  solved by simply installing and running gnome-power-manager. 
However, don't use the latest version from Breezy backports, that one doesn't work.

HTH
Jens

---

### Post by Zyzzyva100 on 2005-11-24
Yea, I tried installing gnome power manager.  I got an error everytime I tried opening it to configure it saying that power managment was not enabled in the screensaver section.  Is this the "not working part".

Assuming I uninstall the version that I have, how might I go about getting a working version.  I am still getting used to where to find what programs.

---

### Post by timetunnel on 2005-11-24
I got the same error, something about DPMS not active. But suspend on lid close worked nonetheless. Only thing that didn't work was suspending automatically after some time of inactitiy.

Jens

---

### Post by quietglow on 2005-11-24
You'll want to change this:

```
# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/lid.sh
```

To either this:
```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/sleep.sh
```

or
```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/hibernate.sh
```


Depending upon whether you want it to sleep or hibernate.

---

### Post by quietglow on 2005-11-24
Oh and I believe that lid.sh script that looks like the most obvious thing to mess with is actually generated by GPM and doesnt actually do anything--I could be wrong but I spent some serious time messing with it on my previous laptop with zero results. Changing the lidbtn script as indicated above did the trick though.

---

### Post by ranf on 2005-11-24
[QUOTE=quietglow]Oh and I believe that lid.sh script that looks like the most obvious thing to mess with is actually generated by GPM and doesnt actually do anything--I could be wrong but I spent some serious time messing with it on my previous laptop with zero results. Changing the lidbtn script as indicated above did the trick though.[/QUOTE]
For me lid.sh runs the screensaver and locks the screen. But it relies on settings made in /etc/default/acpi-support.

---

### Post by timetunnel on 2005-11-24
[QUOTE=quietglow]
```

# /etc/acpi/events/lidbtn
# Called when the user closes or opens the lid

event=button[ /]lid
action=/etc/acpi/sleep.sh
```
[/QUOTE]

I tried that, but it doesn't change a thing, nothing happens when the lid is closed :???: 

Jens

---

### Post by ranf on 2005-11-24
[QUOTE=timetunnel]I tried that, but it doesn't change a thing, nothing happens when the lid is closed :???: 
[/QUOTE]
Try this please: make the last line look like this:
```
action=/etc/acpi/sleep.sh sleep
```

---

### Post by timetunnel on 2005-11-24
[QUOTE=ranf]```
action=/etc/acpi/sleep.sh sleep
```[/QUOTE]
 
Yes! Works now. Many thanks :p 

Jens

---

### Post by Zyzzyva100 on 2005-11-25
Even adding the extra "sleep" after the sleep.sh didn't do it for me.  I even tried removing the gnome power manger tool and the radeontool package.  Nothing at all seems to happen when I close the lid, how can I tell what is actually happening when I close it?

Suspend via fn-f4 still works, but i would really like it to work when i close the lid too.

---

### Post by ranf on 2005-11-25
[QUOTE=Zyzzyva100]Even adding the extra "sleep" after the sleep.sh didn't do it for me.  I even tried removing the gnome power manger tool and the radeontool package.  Nothing at all seems to happen when I close the lid, how can I tell what is actually happening when I close it?

Suspend via fn-f4 still works, but i would really like it to work when i close the lid too.[/QUOTE]
Running this (from a terminal) gives some info. But logging for ACPI related stuff should really be improved.
```
sudo tail -f /var/log/acpid
```

---

### Post by Zyzzyva100 on 2005-11-25
Well, I think I know what the problem is then.  When I press the lid button, I get this:

```
completed event "button/lid LID 00000080 00000005"
[Fri Nov 25 20:09:21 2005] received event "ibm/hotkey HKEY 00000080 00005002"
[Fri Nov 25 20:09:21 2005] notifying client 5963[111:111]
[Fri Nov 25 20:09:21 2005] completed event "ibm/hotkey HKEY 00000080 00005002"
[Fri Nov 25 20:09:21 2005] received event "button/lid LID 00000080 00000006"
[Fri Nov 25 20:09:21 2005] notifying client 5963[111:111]
[Fri Nov 25 20:09:21 2005] executing action "/etc/acpi/lid.sh"
[Fri Nov 25 20:09:21 2005] BEGIN HANDLER MESSAGES
[Fri Nov 25 20:09:21 2005] END HANDLER MESSAGES
[Fri Nov 25 20:09:21 2005] action exited with status 0
[Fri Nov 25 20:09:21 2005] completed event "button/lid LID 00000080 00000006"

```

I have the tpb program installed which allows for the ibm hotkeys to have an on screen display.  I have a feeling that I just need to edit that somehow, because its overriding what I actually want to have happen.

---

### Post by Zyzzyva100 on 2005-11-25
Thanks ranf!  That bit of logging from the acpi was all I needed to see.  Once I figured out that regardless of what I thought I had set, the tpb program was running lid.sh when I closed the lid, I just made a copy of the original lid.sh, and then replaced the contents of it with sleep.sh, rebooted, and it works.

I suppose if In the future I want suspend to disk to work instead I will just replace the contents of lid.sh with hibernate.sh.


Now, anyone know if its possible to make the wireless reaquire any quicker?  I guess it takes about 30 seconds to try to do so now, but hey, if its possible, why not do it faster.  or maybe that is best left to another thread.

---

### Post by hughsient on 2005-11-27
[QUOTE=timetunnel]For me (IBM R52) it was  solved by simply installing and running gnome-power-manager. 
However, don't use the latest version from Breezy backports, that one doesn't work.
[/QUOTE]

It will, if you update the version of HAL to at least 0.5.4. 0.5.5.1 was released recently, and this works really well with g-p-m on ubuntu.

Richard Hughes, g-p-m maintainer.

---

### Post by daller on 2005-12-14
Zyzzyva100>

To be able to solve another thread about a X31, I'd like to know if you are having problem with the CF-cardreader, as described here:

[http://ubuntuforums.org/showthread.php?t=103481](http://ubuntuforums.org/showthread.php?t=103481)

---

### Post by Franko30 on 2005-12-14
[QUOTE=ranf]Try this please: make the last line look like this:
```
action=/etc/acpi/sleep.sh sleep
```[/QUOTE]

Hi,

I tried that on my Dell X1 - it works even without the extra sleep - BUT:

The script seems to be run when closing AND when opening the lid.

So, after resuming it just goes to standby again... :rolleyes:

Cheers

---

### Post by ranf on 2005-12-15
[QUOTE=Franko30]
I tried that on my Dell X1 - it works even without the extra sleep - BUT:

The script seems to be run when closing AND when opening the lid.

So, after resuming it just goes to standby again... :rolleyes:
[/QUOTE]
On my laptop, that I upgraded from Hoary to Breezy, I had two files that reacted on a lid event. Check it out:
```

cd /etc/acpi/events/
grep  lid *
```

---

