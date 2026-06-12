---
title: "Inspiron 6000 won't shut down, suspend or hibernate"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by antar on 2006-11-18
And I believe the three are related.

Occasionally, and actually increasingly frequently, when I try to suspend my laptop in Ubuntu (Dapper), it goes to screensaver, the screen shuts off for a second, and then everything comes right back, and I get an error message directing me to the unhelpful GNOME power management FAQ. The same thing happens with Hibernate.

And then, when I go to shutdown, it will go through the shutdown process, all the way to "Will Now Halt." There it stays, finally getting to the text screen that reports that it's trying to halt, I believe, the LVM (or LVN or something) groups... but it won't go any farther.

I hold down the power button for long enough, and it will turn off, and then when I reboot, Ubuntu acts as if it was shut down properly.

I'd been noticing the shutdown problem would happen occasionally ever since I got Ubuntu a few months ago (end of August) but only recently noticed the suspend/hibernate issue. Again, this isn't all the time, but when I have a problem with suspend/hibernate, it never fails that I have a problem with the shutdown.

I recently flashed my BIOS--updated from A06 to A09--but this problem had been going on long before.

Thanks for the help!

---

### Post by antar on 2006-11-18
Correction: when not going on past "Will Now Halt," it takes me to the text screen, where:

"Will now halt LVM Volume Groups [OK]"

is the LAST thing up.

---

### Post by frogotronic on 2006-11-19
> **antar said:**
> Correction: when not going on past "Will Now Halt," it takes me to the text screen, where:

"Will now halt LVM Volume Groups [OK]"

is the LAST thing up.

If you have an nVidia card (i'm pretty sure i6000 have these)

Make sure VBE is installed

in your xorg.conf file, set (under the DEVICE section for the nvidia card

```
Option "NvAGP" "1"
Option "VBERestore" "1"
```

make your /etc/hibernate/ram.conf file look like this:

[B]# Example ram.conf file for suspending to RAM. Adapt to your own tastes.
# Options are not case sensitive.
# 
# Run "hibernate -h" for help on the configuration items.

### sysfs_power_state
UseSysfsPowerState mem
PowerdownMethod shutdown

##############################################################################
### Some global settings
##############################################################################

Verbosity 0
LogFile /var/log/hibernate.log
LogVerbosity 1
AlwaysForce yes
AlwaysKill yes
# HibernateVT 15
# Distribution debian (or fedora/gentoo/mandrake/redhat/slackware/suse)
# XDisplay :0

##############################################################################
### Scriptlets
###   Scriptlets provide support for doing all sorts of things before and after
###   suspending. The defaults settings here should work for most people, but
###   you may wish to edit these to taste. Consult "hibernate -h" for help on
###   the configuration settings.
##############################################################################

### bootsplash
## If you use bootsplash, also enabling SwitchToTextMode is recommended if
## you use X, otherwise you may end up with a garbled X display.
# Bootsplash on
# BootsplashConfig /etc/bootsplash/default/config/bootsplash-1024x768.cfg

### clock
SaveClock restore-only

### devices
# IncompatibleDevices /dev/dsp /dev/video*

### diskcache
# DisableWriteCacheOn /dev/hda

### fbsplash (enable SwitchToTextMode if you use this)
# FBSplash on
# FBSplashTheme suspend2

### filesystems
# Unmount /nfsshare /windows /mnt/sambaserver
# UnmountFSTypes smbfs nfs
# UnmountGraceTime 1
# Mount /windows

### grub
# ChangeGrubMenu yes
# GrubMenuFile /boot/grub/menu.lst
# AlternateGrubMenuFile /boot/grub/menu-suspended.lst
# BackupGrubMenuFile /boot/grub/menu.lst.hibernate.bak

### hardware_tweaks
# IbmAcpi yes
# RadeonTool yes

### lilo
# EnsureLILOResumes yes

### lock (generally you only want one of the following options)
# LockConsoleAs root
# LockXScreenSaver yes
# LockKDE yes
# LockXLock yes
# LockXAutoLock yes

### misclaunch
# OnSuspend 20 echo "Good night!"
# OnResume 20 echo "Good morning!"

### modules
# UnloadModules snd_via82cxxx usb-ohci
# UnloadAllModules yes
UnloadBlacklistedModules yes
LoadModules auto
# LoadModulesFromFile /etc/modules

### modules-gentoo
# GentooModulesAutoload yes

### network
# DownInterfaces eth0
# UpInterfaces auto

### pcmcia
# EjectCards yes

### programs
# IncompatiblePrograms xmms

### services
# RestartServices postfix
# StopServices alsasound
# StartServices aumix

### vbetool
EnableVbetool yes
# RestoreVbeStateFrom /var/lib/vbetool/vbestate
VbetoolPost yes
# RestoreVCSAData yes

### xhacks
SwitchToTextMode yes
# UseDummyXServer yes

### xstatus
## This can be set to gnome, kde or x:
# XStatus gnome
# XSuspendText Preparing to suspend...
# XResumeText Resuming from suspend...
## When using XStatus x, and you have xosd installed:
# XosdSettings --font -misc-fixed-medium-r-semicondensed--*-120-*-*-c-*-*-* --colour=Green --shadow 1 --pos bottom --align center --offset 50[/B]

try it now...


-CH

---

### Post by antar on 2006-11-19
I didn't spring for the NVidia card. Just got the simple Intel 915 chipset.

---

### Post by frogotronic on 2006-11-19
> **antar said:**
> I didn't spring for the NVidia card. Just got the simple Intel 915 chipset.

ok, you're probably in better shape.  Most of the suspend/hibernate problems seem to eminate from the binary nVIDIA drivers (required for twinview (second vga output) and for openGL rendering.

Go to synaptic and get the "915resolution" package (this is written to ineteract with the intel915 graphics chipset.  Try the mod to the suspend script and see if you can get suspend-to-RAM to work.

-CH

---

### Post by antar on 2006-11-29
> **cement_head said:**
> Try the mod to the suspend script and see if you can get suspend-to-RAM to work.


How exactly do I do that?

Thanks again.

---

### Post by frogotronic on 2006-12-10
> **antar said:**
> How exactly do I do that?

Thanks again.

sorry, thought I was email subscribed to this thread.

To edit the Suspend-to-DISK (Hibernate) function:

```
sudo gedit /etc/hibernate/hibernate.conf
```

or 

To edit the Suspend-to-RAM (Suspend) function:

```
sudo gedit /etc/hibernate/ram.conf
```

---------------------------------------------

Post these conf files and we'll see if there is something obvious

---

### Post by antar on 2006-12-14
Interesting. I don't HAVE the hibernate folder in etc, nor do I have ram.conf anywhere on my file system.

But how will fixing those fix the laptop shutdown problem? Doesn't it seem like the problems are related?

Thank you, immensely, by the way, for your help.

---

### Post by frogotronic on 2006-12-14
Run Synaptic and install **hibernate** and **hal**

Reboot your machine and then try hibernate.

- CH

---

### Post by antar on 2006-12-15
Installed Hibernate...

Let's see if that fixed the problem.

Unfortunately, I won't know for sure for probably several weeks--as with every problem that only occurs occasionally, you can't really prove it's been fixed, only that it hasn't been.

Thanks again.

-G

---

### Post by frogotronic on 2006-12-15
let us (the ubuntu forum) know if this fixes your problem.

Later,
- CH

---

