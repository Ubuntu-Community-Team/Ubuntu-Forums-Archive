---
title: "Dell 640m display does wake from suspend but everything else does"
date: 2007-03-10
forum: Hardware &amp; Laptops
---

### Post by ubuntalicious on 2007-03-10
Hey guys.  I have Edgy on a new dell 640m and when I wake the system from suspend, the hdd light flashes for a bit and then nothing happens.  Screen is blank, keys are unresponsive, etc.  The fan seems to come on here and there, so I think that a lot of stuff is getting powered up, but then something hangs.

Is anyone else having this problem?  Suggestions?


Thanks,
Ben

---

### Post by Paerez on 2007-03-10
i have a 600m, I had to make changes to the file "/etc/default/acpi-support"

here is the entire contents of my file:
```

# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
# ACPI_HIBERNATE=true

# Comment the next line to disable the use of the hibernate script for
# driving the suspend-to-disk process.
ACPI_USE_HIBERNATE_SCRIPT=true

# Arguments to pass to the hibernate script if ACPI_USE_HIBERNATE_SCRIPT is set
#ACPI_HIBERNATE_ARGS="--config-file=/etc/hibernate/suspend2.conf"

# Enable the following to use the hibernate script for suspend to RAM also.
# Enabling this means that most of the rest of this file is irrelevant.
# Add your tweaks to /etc/hibernate/ram.conf instead.
#ACPI_USE_HIBERNATE_FOR_STR=true

# Arguments to pass to the hibernate script for suspend to RAM if
# ACPI_USE_HIBERNATE_FOR_STR is enabled, above.
#ACPI_HIBERNATE_STR_ARGS="--config-file=/etc/hibernate/ram.conf"

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

### Post by ubuntalicious on 2007-03-10
I see a number of settings differences between our files.  Before I just replace mine with yours, do you remember specifically what I need to change?

Thanks,
Ben

---

### Post by Paerez on 2007-03-10
the following are the ones I think are important:

save_vbe_state
post_video

try those first.

Also copy the file to your desktop or something just in case ;)

---

### Post by ubuntalicious on 2007-03-11
Okay, I've tried just those two lines, and the whole file, and still no dice.  It worked once, I think, but has hung all other times.  Thanks for posting that, but it doesn't work for me.  :( 

Any other suggestions?

---

### Post by Paerez on 2007-03-11
after you edit the file, you have to restart acpi by running:
sudo /etc/init.d/acpi-support restart
or by rebooting your computer.

---

### Post by ubuntalicious on 2007-03-11
I didn't know about the restart command, so that's cool.

Nevertheless, I did restart after each change that I made.

---

### Post by Paerez on 2007-03-12
yeah usually when you change a configuration file, to see the effects you have to run the init.d script with the "restart" command to get it to read the config file. You can check out all the scripts in that folder. A lot of the time it saves you a restart.

Well even though we didn't get it working at least you learned something....

Oh by the way, what graphics car do you have?

can you print the output of:

lspci

and

grep Driver /etc/X11/xorg.conf

then I'll have more info.

---

### Post by kolinab on 2007-03-12
The problem you're describing is identical to what I am experiencing on my 630m. I hadn't thought to describe it that way, but I think you're right - it is the display that is not waking up.

I wonder if there is a keystroke combination I can execute that will shut the system down - if it works then that would confirm that everything but the display is working, before troubleshooting further. Anyone know what I could do to try that?

---

### Post by Paerez on 2007-03-12
Here are a couple ways to tell the system to shut down or restart:


CTRL+ALT+F1 then CTRL+ALT+DEL

CTRL+ALT+F1 then hit the Power button under the monitor

while holding (Left ALT + Prnt Scrn) press S then U then B

---

### Post by kolinab on 2007-03-12
Super - thanks! I'm gonna try this soon and then will be a step ahead troubleshooting this problem.

---

### Post by tschneiter on 2007-03-12
On a 640m here - 
I was having trouble with this too, until I added (in edgy) "blacklist video" to the blacklist found at /etc/modprobe.d/blacklist. This also allowed me to adjust the screen brightness using fn+arrow keys. 

Further, upon upgrading to feisty, I needed no such hack to make things work. Perhaps you should consider the upgrade?

---

### Post by ubuntalicious on 2007-03-18
> **tschneiter said:**
> On a 640m here - 
I was having trouble with this too, until I added (in edgy) "blacklist video" to the blacklist found at /etc/modprobe.d/blacklist. This also allowed me to adjust the screen brightness using fn+arrow keys. 

Further, upon upgrading to feisty, I needed no such hack to make things work. Perhaps you should consider the upgrade?



Okay, that's good to know that it's okay on Feisty.  I have already done the video module blacklist, which fixed my brightness, but didn't fix my standby.

So here's a noob question: is it wise to upgrade to Feisty even though it isn't really out until April?


Thanks,
Ben

---

### Post by ubuntalicious on 2007-03-18
> **Paerez said:**
> yeah usually when you change a configuration file, to see the effects you have to run the init.d script with the "restart" command to get it to read the config file. You can check out all the scripts in that folder. A lot of the time it saves you a restart.

Well even though we didn't get it working at least you learned something....

Oh by the way, what graphics car do you have?

can you print the output of:

lspci

and

grep Driver /etc/X11/xorg.conf

then I'll have more info.


Sorry for the delay in response, I've been really busy this week.  Anyhow, here is the output that you requested:

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```


```
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "i810"

```

By the way, I had problems setting up graphics when I installed Edgy and had to run sudo dpkg-reconfigure xserver-xorg to set up my graphics.  I don't know if it's relevant, but I thought I'd mention it.


Thanks again,
Ben

---

### Post by kolinab on 2007-03-18
> **ubuntalicious said:**
> Okay, that's good to know that it's okay on Feisty.  I have already done the video module blacklist, which fixed my brightness, but didn't fix my standby.

So here's a noob question: is it wise to upgrade to Feisty even though it isn't really out until April?


Thanks,
Ben

I don't think it would be especially unwise to upgrade . . . but I'm going to wait until the official release comes out and the dust settles a bit before I do so.

---

### Post by ubuntalicious on 2007-03-18
okay, another update...

I tried parez's suggestion to try rebooting when it comes out of sleep.  I woke it up, the screen stayed blank, and then I pressed ctrl-alt-F1 and then ctrl-alt-delete and lo and behold, it rebooted.

So it appears that the problem lies primarily with the display.

~Ben

---

### Post by tschneiter on 2007-03-18
Unfortunate that your display does not seem to feel like waking up... After blacklisting video it worked for me. 

Anyways, Ive found better support for just about everything under feisty. I am not using this as a mission-critical machine, so any instability wouldnt matter much, however, I have not found any additional instability with feisty. I would reccomend the upgrade, even if it is still 'alpha.'

---

