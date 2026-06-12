---
title: "Thinkpad x60 &amp; 7.10"
date: 2007-12-24
forum: Hardware &amp; Laptops
---

### Post by shmoooo on 2007-12-24
hey,

While most of the features work out of the box, resume after suspend to ram works only half the time. Sometimes the screen stays dark, sometimes wifi is broken afterwards, and so on.

Someone using Ubuntu on a x60 and having similar issues?

---

### Post by corte123 on 2008-01-07
i have a thinkpad x60 model 6363 running gutsy , suspend an hibernate works always 100%

---

### Post by realbiga on 2008-01-10
im on an X60 6365 tablet and have a similar problem. When i resume from disk wifi doesnt work. restarting network manager (sudo /etc/init.d/dbus restart) doesnt resolve.

Cortel123:
   which driver are you using for your wifi? im using a snapshot of madwifi since the latest release doesnt support the atheros 5418 yet.

---

### Post by sudo_t43p on 2008-01-22
> **realbiga said:**
> im on an X60 6365 tablet and have a similar problem. When i resume from disk wifi doesnt work. restarting network manager (sudo /etc/init.d/dbus restart) doesnt resolve.

Cortel123:
   which driver are you using for your wifi? im using a snapshot of madwifi since the latest release doesnt support the atheros 5418 yet.

I have the same problem. Ain't sure but the black screen could be due to Compiz. Do you run Compiz / Beryl? 

BR,
Chrisse

---

### Post by Junyulive on 2008-02-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/159935](https://bugs.launchpad.net/ubuntu/+bug/159935) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				My audio card doesn't work.

---

### Post by Yellow Pasque on 2008-02-26
> **Junyulive said:**
> My audio card doesn't work.

```
sudo gedit /etc/modprobe.d/alsa-base
```
Add this line:
```
options snd-hda-intel model=thinkpad 
```

If that doesn't work, try upgrading to the latest version of ALSA:
[http://ubuntuforums.org/showthread.php?p=4298894#post4298894](http://ubuntuforums.org/showthread.php?p=4298894#post4298894)

---

### Post by rshields on 2008-02-26
> **shmoooo said:**
> hey,
While most of the features work out of the box, resume after suspend to ram works only half the time.

Same issue here on an X60s, currently unresolved. See [this thread]("http://ubuntuforums.org/showthread.php?p=4194051"). Let me know if you find a solution.

---

### Post by rshields on 2008-02-26
> **sudo_t43p said:**
> I have the same problem. Ain't sure but the black screen could be due to Compiz. Do you run Compiz / Beryl? 

BR,
Chrisse

Oh hi

I have gone back to xfwm4 and it seems to have fixed my freezing during resume/black screen problem. Thanks for the tip.

EDIT: actually no, it's still freezing sometimes during resume :(

---

### Post by zeiz on 2008-02-26
I got 7.10 on Thinkpad i1452 (celeron=365MHz, 66MHz ram (non IBM) =256MB...etc :( + faulty FDD, dropped repeatedly at airports in 10 years...everything worked perfect. I switched to PCBSD because this relict runs it faster. 
Maybe you got faulty media for install?

---

### Post by rshields on 2008-02-26
Your laptop is completely different hardware to the X60 so is unlikely to be affected by the same problems if it's driver related. Does your laptop run compiz? Since there appears to be several of us having the same problem then I doubt it's related to the installation media.

---

### Post by zeiz on 2008-02-26
It would be a miracle...of course I even didn't try. But all the features supported by 10 y.o. laptop worked (it looked that LIve mode was even faster than install). I used to have problems with selfburned media on my desktop so...sorry if I didn't guess:)

---

### Post by arist0tle on 2008-02-27
I have the same setup and having (or have had) most of those issues. Are the windows on some the apps you use larger than the screen. That is the one that is driving me crazy. Overall, Gutsy has brought down my opinion of ubuntu. I am investing a lot of faith in Hardy to change this. There are a lot of things that I really love about Ubuntu and I would hate to lose those things.

---

### Post by schmolch on 2008-02-28
I'm using a X60T and after some tweaking of acpi-support suspend-to-ram seems to work fine now.

I don't remember what i changed, here is the whole file.

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
MODULES="uhci_hcd"

# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST=""

# Should we save and restore state using the VESA BIOS Extensions?
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true    # I CHANGED THIS !!!

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
LOCK_SCREEN=false

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
#DISABLE_DMA=true

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
# hangs on some machines
ENABLE_LAPTOP_MODE=true

# Spindown time on battery
SPINDOWN_TIME=12

---

