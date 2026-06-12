---
title: "Getting resume to work on Compaq 6910p"
date: 2008-06-22
forum: Hardware
---

### Post by rickcr on 2008-06-22
I followed what this guide mentioned in regard to my acpi settings 
[http://jkyamog.blogspot.com/2007/12/linux-install-on-hp-6910p-using-ubuntu.html]("http://jkyamog.blogspot.com/2007/12/linux-install-on-hp-6910p-using-ubuntu.html") Closing the lid or manually putting the computer into suspend mode seems to work, but it doesn't always resume when I press the power button. It seems like it 'tries' to resume as in the power button turns a solid green and the fan starts to spin.. problem is the screen stays black. Sometimes however it does work, so I'm confused what the issue is.

Thes settings changed were:
SAVE_VBE_STATE=false
POST_VIDEO=false
DOUBLE_CONSOLE_SWITCH=true

The final acpi-support setting looks like;


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
#orig: SAVE_VBE_STATE=true
SAVE_VBE_STATE=false

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#orig POST_VIDEO=true
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
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

---

### Post by damphoud on 2008-06-22
System specs?

---

### Post by rickcr on 2008-06-22
Wasn't sure the easiest way to get system specs so I ended up installing "hardinfo" I posted the results here:

[http://www.learntechnology.net/hardinfo_report.html]("http://www.learntechnology.net/hardinfo_report.html")

I do hope someone can help because I really need this suspend/resume working. I have a lot of stuff that I'll be doing during the day at work on the laptop and would like to bring the laptop home at night and continue without having to boot back up and restore everything I had opened.

Apparently suspend/resume should work on this laptop so hopefully it's just something simple I need to do?

---

### Post by rickcr on 2008-07-02
Just bumping in case anyone has some other ideas I can try. It's very frustrating to not have a way to suspend and resume on my laptop.

---

### Post by _sphinx_ on 2008-07-02
I have the same kind of problem but I have a solution that work sometimes, but I am not sure that it will work on your laptop. I am using Dell inspiron. Try pressing Fn+LCD key in your laptop when you in the situation of blank screen. In my laptop the LCD key is attached with F7, so I press Fn+F7. It helps me many time but not always.

---

### Post by phidia on 2008-07-02
Maybe you already looked at the settings in System>Preferences>Power Management but if you haven't that's one simple thing to do.

---

### Post by rickcr on 2008-07-02
> **_sphinx_ said:**
> Try pressing Fn+LCD key in your laptop when you in the situation of blank screen. In my laptop the LCD key is attached with F7, so I press Fn+F7. It helps me many time but not always.

I think I've tried every possible key combo I could. FN+{everything} :) Basically the keyboard seems completely unresponsive. 

Not sure how related this is, but when I do try to wake it from suspend (by pressing the power button), the fan starts up pretty fast and actually reminds quite fast until I turn the puter off with the power button.

---

### Post by rickcr on 2008-07-02
> **phidia said:**
> Maybe you already looked at the settings in System>Preferences>Power Management but if you haven't that's one simple thing to do.

Checked those settings several times. It seems to be suspending ok, just not coming awake properly.

---

### Post by jkyamog on 2008-07-18
rickr,

For gutsy sometimes it does not resume quickly.  To make it resume quickly, I click the power button a few times.  This seems to trigger some acpi event.  Don't press too long or too quick intervals as it will be interpreted as a shutdown.  I also noticed that its going to resume soon when the mute (orange) led lights up.

I just upgraded to Hardy today, so far it seems to resume just fine.

---

### Post by rickcr on 2008-10-25
I'm still so frustrated with this. Suspend sometimes work, but more often than not I have to reboot. I'm not sure what else to try?

---

### Post by zzottt on 2008-11-07
ya I gave up on it 	:-({|=

now I just hit FN+F3 and it sleeps and resumes from that without problem. If I just close the lid or choose to Suspend from the menus inside Ubuntu it doesn't work.


FN+F3 works 90% of the time. Sometimes networking fails when it comes back and so I just ctrl+alt+backspace then log in again and then it works

---

### Post by IQRules on 2008-12-21
Do you use WICD (wireless connect)? If so, before standby, try disconnect it from WICD?

---

### Post by rickcr on 2008-12-30
I was hoping 8.10 would help, but it made things worse. Using either the new default acpi-support that 8.10 created, or the one that I modified - neither helps. In fact things seem worse with 8.10. I can't seem to even shutdown correctly. I just get a hanging cursor on a black screen. No key combo gets me out of it, I have to hard reboot. pain in the a**s.

Anyone else with ideas? (other than stick to my Mac Book Pro which doesn't have these issues:)

---

### Post by rickcr on 2008-12-30
... actually shutdown does work if I use the "log out" icon but not if I use 'shut down' from the system menu.

---

### Post by mizu12 on 2009-01-30
Hey, I just realized that a our problem might be solved by a BIOS upgrade.

The relnotes for version F.17 states on HP's website:

"- Fixes an issue where closing the notebook lid and leaving the notebook idle for several minutes causes the LCD display to be blank when the notebook lid is re-opened. "

Didn't try, but hope this helps.

Anyway my fans are "always on" after last kernel changes (2.6.17-11) on Intrepid....

---

### Post by ssri on 2009-05-22
> **mizu12 said:**
> Hey, I just realized that a our problem might be solved by a BIOS upgrade.

The relnotes for version F.17 states on HP's website:

"- Fixes an issue where closing the notebook lid and leaving the notebook idle for several minutes causes the LCD display to be blank when the notebook lid is re-opened. "

Didn't try, but hope this helps.

Anyway my fans are "always on" after last kernel changes (2.6.17-11) on Intrepid....

Had the same problem.  It seems that the bios update worked, for now...

---

### Post by ssri on 2009-06-11
Nope, after awhile, the bios update did nothing and the problem came back.  Resuming after suspension is frightfully slow with all of the daemons simultaneously writing to the disk causing massive slowdowns that last for 5mins or more.  Especially when firefox is one of the programs that I saved when going into suspend mode.

---

