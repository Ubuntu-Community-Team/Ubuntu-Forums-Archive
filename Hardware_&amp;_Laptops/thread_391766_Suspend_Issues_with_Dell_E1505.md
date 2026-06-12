---
title: "Suspend Issues with Dell E1505"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by legzelda on 2007-03-23
Like many other E1505 laptop users, I have had little success getting my laptop to consistently resume after suspending it.  However, after patching my kernel to use suspend2 and modifying /etc/default/acpi-support to the included settings, I have made interesting headway.  When I log out and suspend my laptop, it will successfully suspend and resume from suspend-mode.  However, if I suspend when I am logged-in, my laptop will successfully suspend, but when attempting to resume from suspend, the screen will often come up with a blinking cursor and then go blank, or just simply be blank.  No key-combinations seem to work, including Ctrl + Alt + Backspace, Ctrl + Alt + Delete, and Alt + Ctrl + F1.  The sleep combination on my laptop (Fn + Esc) does not work, either.  Unfortunately, the only option I have at this point is to reboot.  

I am thinking I must have something running when I am logged-in that does not allow my computer to successfully resume from standby.  Are there any suggestions about what I can do to solve this problem?


[PHP]# Comment the next line to disable ACPI suspend to RAM
ACPI_SLEEP=true

# Comment the next line to disable suspend to disk
ACPI_HIBERNATE=true

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
MODULES_WHITELIST="fglrx"

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=false

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
RADEON_LIGHT=false

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
DISABLE_DMA=true

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
ENABLE_LAPTOP_MODE=false[/PHP]

---

### Post by tschneiter on 2007-03-23
For me (e1405), the  solution was to add "blacklist video" to /etc/modprobe.d/blacklist. After that, everything seemed to work.

Also, it worked by default for me in feisty.

---

### Post by legzelda on 2007-03-24
I already had "blacklist video" in that file, but thanks for the suggestion.  I still have issues with going into standby when logged-in.

---

### Post by dimbulb1024 on 2007-03-24
Although I have a Dell 6000 the models are close and I also had the same problem.
The one thing I started doing was to unplug my usb mouse prior to suspending and then plug it back in after resuming.
This was the trick that cured my problem.

---

### Post by edgimar on 2007-05-07
You might take a look at [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/40621/comments/44](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/40621/comments/44)

There are two things I needed to modify in order for it to work for me (as mentioned in the above link).

I am using Feisty.

---

### Post by n&amp;70{s&gt;,PGh on 2007-05-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/40621](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/40621) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				"There was only one other needed change -- according to bug #23497 comments 5 and 6 -- adding /etc/acpi/suspend.d/20-i8042-input.sh and /etc/acpi/resume.d/40-i8042-input.sh , to prevent the mouse and keyboard from locking up after resume."

So you had to create those two files? Did you have to write anything in them?

---

### Post by edgimar on 2007-05-10
in bug # 23497, comment 5, there is a patch which contains the text that goes into those two files.  Note that based on comment 6, the names of the files are different than the names specified by the patch.  In short, read carefully comment 5 and 6, and all should be clear(er).

---

