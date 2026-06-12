---
title: "Hibernation and ATI Radeon Express 200M broken"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by RavanH on 2007-04-19
Hi,

I have a Packard Bell EasyNote laptop with ATI Radeon Express 200M pcie. Directly after installing Feisty (beta, at the time) hibernation worked but now, after messing with the ATI drivers trying to get desktop effects running (and failed :( ), I notice that hibernation doesn't work anymore...

After clicking 'Sleep' the system starts the hibernation routine but after a short while just goes back into the just (seemingly) closed session as if nothing happened!?!

Anyone know how to get hibernation back again?

Thanks,
-- Allard.

**Related entries in config files**

*xorg.conf*
```
...
Section "Monitor"
	Identifier   "Generic Autodetecting Monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Radeon Xpress 200M"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Radeon Xpress 200M"
	Monitor    "Generic Autodetecting Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "disable"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

```

*acpi-support*
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
STOP_SERVICES="mysql "

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=true

```

---

### Post by RavanH on 2007-04-19
Just before going back into the previous session, the screen shows some text output for a very short time. The last line of that output is something like:
"Cannot find swap device. Try swapon -a"

So I did that in a Terminalscreen: and it  returned and error (in dutch which roughly translates to) "swapon: cannot find status of /dev/disk/by-uuid/f038c089-c1b5-4f87-a470-3d848118ba7b: File or folder does not exist"

And indeed, the partition I had set up at installation time to be swap has a different uuid :( so what's happening here? Is my Ubuntu installation running without swap? That would explain why the System Monitor always reports "Swap memory: 0 bytes of 0 bytes 0.0%" (again a translation from dutch)...

If I open GParted, it showes my swap partition but it is unlocked. Richt-clicking it gives me the option "use as swap" (again translation, sorry) and when I choose that option, it returns an error saying something about it being "in use" but the lock appears after that.

Now, hibernate seems to work! Only some errors show in the text screen-output of which this one attracts my attention:
"swsusp: not enough free memory"
But the system shuts down.

Starting the system up again, I have to log into my session and all opened programs are closed. It turned out to be a normal boot, and not a resume from hibernation... 

Then checking GParted again: the whole swap partition is deleted and shown as "unknown" !?!?

I am afraid: is there something seriously wrong with Feisty here? Or what? :confused: 

Thanks for any suggestions,
-- Allard

---

### Post by RavanH on 2007-04-19
Ok, the story continues...

Based upon some guess-work and to threads on these forums [http://ubuntuforums.org/showthread.php?p=1140244&page=2&highlight=swsusp](http://ubuntuforums.org/showthread.php?p=1140244&page=2&highlight=swsusp) and [http://ubuntuforums.org/showthread.php?t=400673&highlight=uuid](http://ubuntuforums.org/showthread.php?t=400673&highlight=uuid) , I did the following to restore swapping on my system because apparantly somewhere something has gone wrong with my swap partition setup... 

Logged in as root:

1. I opened GParted (System > Manage > GNome Partition Editor) and right-clicked the partition that was intended to be swap but now marked "unknown" (see previous post) and selected 'Format as > Swap'. Then clicked 'Edit > Apply'.

2. Right-clicked the newly formatted swap partition and selected 'Swap on', applied again and closed GParted.

3. Went to Locations > Computer > Filesystem > /dev/disk/by-uuid/ and by right-clicking and selecting each of the symlinks in that folder, found which uuid pointed to the partition I had just assigned as swap (2). Then right-clicked the symlink, chose 'Rename...' and hit Ctrl+C to copy the uuid to clipboard. Closed the window (without changing the uuid ofcource!).

4. Opened a Terminal screen and entered the command: ```
sudo gedit /etc/fstab.xt-editor
``` and found in the Text-editor the line where is said
```
UUID=.....some-wrong-uuid.... none            swap    sw              0       0
``` and pasted the new uuid over the old one with Ctrl+V. Then Ctrl+S to save the change and closed the editor again.

5. Then entered in the Termina screen: ```
sudo gedit  /etc/initramfs-tools/conf.d/resume
``` and pasted the new uuid again over the old one after RESUME=UUID=... Then saved the changes again.

6. Then entered in the Terminal Screen this command:
```
dpkg-reconfigure initramfs-tools
```

7. After all that, first rebooted the system and checked if swap use was normal again by opening System Monitor (System > Manage > System Monitor) on the tab Graphs: it said Swap 0 bytes of 1.6 GB...

Ffffewwww.... Swapping has been restored again :) ... Only, hibernation still does strange things... Now the system shuts down alright without any error messages. Only after restore, the system hangs within the first minutes of operation.

---

### Post by swisscow on 2007-05-03
This was exactly the problem I had, though I suspect it was my fault that it occured because I was playing around with other distributions and then restoring partitions using partimage.

Anyway your solution worked a treat, can hibernate (lots of strange messages but it works!) and suspend seems ok as well. Haven't given it the 15 minutes of use yet, but so far so good.

Thanks very much!

---

