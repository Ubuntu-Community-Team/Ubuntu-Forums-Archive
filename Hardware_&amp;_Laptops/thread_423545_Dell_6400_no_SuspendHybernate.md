---
title: "Dell 6400 no Suspend/Hybernate"
date: 2007-04-26
forum: Hardware &amp; Laptops
---

### Post by Neuralgia on 2007-04-26
pAfter uograding from Edgy, I lost a whole bunch of things (beryl doesn't work anymore :(, links from evolution don't open Firefox, etc)

But something I used all the time (it's a laptop, it's supposed to be used) is the Suspend/Hibernate features.

Everytime I use both, my screen goes black, but after that, can go back to my OS... I have to press the power button, to force a shutdown and turn the laptop again.

Again, in edgy, it worked perfectly.

My acpi-support looks like this
> 
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
ENABLE_LAPTOP_MODE=true

Any ideas?

---

### Post by EarthlyDilemma on 2007-04-26
I know that on my Dell Inspiron 5100 I have to go into /boot/grub/menu.list, 
locate the kernel section and add:

     "acpi_irq_balance"

 AND change "splash" to:

     "no_splash"

Remove the quotes for all of the above.

---

### Post by Neuralgia on 2007-04-26
didn't work... it's starting to get annoying :(

---

### Post by skorps on 2007-04-27
I have found a solution... thanks to zarmando : 

[http://ubuntuforums.org/showpost.php?p=2520291&postcount=38](http://ubuntuforums.org/showpost.php?p=2520291&postcount=38)

That seems to work very fine for me ;)
I think that is the line "double console switch" wich needs to be uncomment.

Good luck.

---

### Post by Neuralgia on 2007-04-27
sorry, not for me...

did you did a fresh Feisty install or did you upgraded?

---

### Post by skorps on 2007-04-28
It's a fresh install. A crash in the upgrade broke my system, so I decided to make a fresh install...

Maybe you can try that : [http://ubuntuforums.org/showthread.php?p=2016799](http://ubuntuforums.org/showthread.php?p=2016799)

That was resolving the problem for some people but it was about feisty's betas. In any case, I think the issue is on the acpi-support file, but as I'm not an expert, I can't help you more :(

---

### Post by red_five on 2007-05-03
Check out the file ```
/etc/initramfs-tools/conf.d/resume
``` then do ```
ls -la /dev/disk/by-uuid
``` Pick the entry that matches your swap partition, and make sure it matches the entry in the resume file. If it doesn't match (and it probably won't if you had to recreate your paritions), then copy and past the correct uuid into the resume file. Also, check your ```
/boot/grub/menu.lst
``` for a resume partition under the defoptions section; it should read something like ```
defoptions=quiet splash vga=773 resume=/dev/hda2
``` If not, you can simply add the resume=... line.

---

