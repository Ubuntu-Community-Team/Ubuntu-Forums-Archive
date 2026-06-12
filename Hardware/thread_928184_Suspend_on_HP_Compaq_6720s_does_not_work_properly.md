---
title: "Suspend on HP Compaq 6720s does not work properly"
date: 2008-09-23
forum: Hardware
---

### Post by majikins on 2008-09-23
Hello

Running Ubuntu 8.04.

I'm having a problem with the suspend function on my laptop in two ways:

1) when I manually suspend(click on quit and then suspend), and then press the power button to get back up, I need to press 'ctrl-alt-f1' and then 'ctrl-alt-f7' to get to the screensaver authentication screen(otherwise the screen stays black). If I don't do this, waiting for a random amount of time will eventually bring up the screen.
2) when I close the lid, the laptop will automatically suspend but when I open the lid and press the power button, I can hear the hard drive wind up but the screen stays black.  I tried to wait for some time to see if the screen lights up but in vain.  

Is there a way I can get the suspend function to work perfectly?

ie - ideally when I shut the lid, suspends as it does now, and like an apple laptop :-) starts up in good time when I open the lid(3-5 seconds)

Appreciate any help!

Thanks

---

### Post by majikins on 2008-09-26
anyone?

---

### Post by xeth_delta on 2008-09-26
Funny you should mention  this.
For what it's worth, I have also noticed a slight delay until the desktop is back on screen, say 30 - 40 seconds from pressing the power button/opening the lid. This on a Macbook, and I believe that's the only issue with suspend right now on my machine.

From what you mentioned about the button combinations, I guess this behaviour is fixable. I will post  if I find out anything, as I would also be interested in improving this.

---

### Post by majikins on 2008-09-27
Thanks! Coming from an apple platform I miss some of the conveniences.  But the benefits on this platforms are also good - just have to fix the quirks.

---

### Post by xeth_delta on 2008-09-27
> **majikins said:**
> Thanks! Coming from an apple platform I miss some of the conveniences.  But the benefits on this platforms are also good - just have to fix the quirks.

Indeed, it seems to me like a minor inconvenience, too. It will get fixed :) I really would not change Linux over other OS, especially not because of something as small as this.

Anyway, the search for the solution starts.

---

### Post by majikins on 2008-10-13
Ok found out something.  

Seems if I ensure that my network cable is out for a couple seconds before suspending:

1) via function key
2) quit button and suspend

then when I press the power button after lifting the lid, the password prompt appears about 2-4 seconds afterwards.

Any other combination will either have the prompt appear after a random amount of time or not at all.

Anyone have any ideas?

---

### Post by xeth_delta on 2008-10-14
Now that I'm using suspend quite frequently, I have noticed that the delay evident when I'm using a wireless network. When in regular cable network, the computer seems to resun much quicker.

I'll have more observations by the end of the week.

---

### Post by majikins on 2008-10-19
This thread seems to have some interesting information:

[http://ubuntuforums.org/showthread.php?t=665772](http://ubuntuforums.org/showthread.php?t=665772)

going to try them out and post back - nothing on closing of the lid tho.

---

### Post by lores on 2008-10-23
Hey!
I've a similar problem with my HP 6720s - usually when I resume from sus-to-ram, I don't get the backlight neither, yet it helps to just press CTRL and F7 - anyway, it's 2x shorter than CTRL F1 and CTRL F7... Besides, I sometimes don't have this issue at all, ie. sometimes I get to see the screen instantly.

PS
If the time of sus-to-ram is short, then I usually get to see the desktop; if it's longer (say, a few hours), I have to press CTRL F7 and I additionally get a message saying the computer had failed to suspend (or hibernate, if sus-to-hd), although it actually succeeded.

---

### Post by majikins on 2008-10-29
Hi Lores

Did you mean ctrl-alt-F7?   

I've tried that but it does not work for me - still takes about 40secs to about 2 mins to get to the login screen.  In da meantime - I've been fiddling with the /etc/default/acpi-support file with these settings:

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
# SAVE_VBE_STATE=true

# The file that we use to save the vbestate
VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
#POST_VIDEO=true

# Save and restore video state?
SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
# USE_DPMS=true

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
# hangs on some machines
# ENABLE_LAPTOP_MODE=true

# Spindown time on battery
SPINDOWN_TIME=12

------

This seems to have made the response time better 30 seconds but not perfect.

I now find that if my network cable is plugged in, login screen is almost instantaneous.  

I've tried doing a /etc/init.d/network down before suspend but that does not work(logic indicating that suspend is looking for a network connection to resume and if it does not find it, hangs for awhile)

Eventually get there! :guitar:

---

### Post by majikins on 2008-10-31
Ok after rebooting the lappie after a VERY long time of uptime, Lores technique really works well!  Thanks Lores!

---

### Post by Gnuus on 2008-10-31
I have a Compaq Presario CQ50 and when I put it to sleep it never wake's up. I can hear the hard drive spinning but the screen stays black.

Even restarting will not help, I have to remove the battery and put it back in again, before the screen starts working.

I tried all the suggestions mentioned in this thread, but nothing works for me.

I'm using the brandnew Ubuntu 8.10!!!

---

### Post by majikins on 2008-10-31
Hi Gnuus

It would be best for you to start a new thread with your model laptop in the subject line.  Then anyone who has this model can follow the thread.

Best of luck.

S

---

### Post by xeth_delta on 2008-11-02
Just upgraded to Intrepid Ibex, the computer seems to come faster from suspend than before. I will try it more intensively this week at the University and post my conclusions.

One word of caution, though, for people using KDE 3 in 8.04 and which would prefer to keep it for a while longer. (K)Ubuntu 8.10 does not have KDE 3 anymore, it is replaced by KDE 4.

---

### Post by xeth_delta on 2008-11-04
I can confirm that suspend is working much better in Intrepid Ibex. Resume from suspend is almost instantaneous, this on my system, a MacBook 2.1. I have to make sure the madwifi driver is unloaded before suspending and reloaded after resuming.

---

### Post by majikins on 2008-11-05
Thats good to hear!  Except for the suspend, which is now better, I'm loath to upgrade(meaning do a fresh install since I don't believe in doing the upgrade path from existing base) since I'm also going to need to install all my other programs and get the settings just right.  I'd also rather wait for a month or two before making the move. 

Hardy is working like a dream for me now and I love it.

---

### Post by xeth_delta on 2008-11-06
> **majikins said:**
> Thats good to hear!  Except for the suspend, which is now better, I'm loath to upgrade(meaning do a fresh install since I don't believe in doing the upgrade path from existing base) since I'm also going to need to install all my other programs and get the settings just right.  I'd also rather wait for a month or two before making the move. 

Hardy is working like a dream for me now and I love it.

That might be a wise choice for now, especially if you don't have much free time and if your system works great (barring suspend-resume time). These way you could avoid any eventual teething problems. 

I have been upgrading from existing base since Feisty or Gutsy without big problems, except the usual recompilation of sound and wireless drivers, reconfiguring remote and webcam. Of course, also getting used to KDE 4 (which I really like now) and updating Compiz Fusion :D

But I do see your point in doing a clean slate installation, if I had the time and patience these last days, I would probably have done it too.

---

### Post by majikins on 2008-11-27
Just updating.

Had some problems with wifi connections with network-manager(it was erratic) and after some research, decided to remove and install wicd.

What a difference! resume after suspend now just works. And even though I still have a problem with wifi as I am running the driver natively and still have to sort out, everything else is painless.

However some reading indicates that wicd can be worse than network-manager for some people.  All I know is that it works for me!

---

### Post by majikins on 2008-11-28
updated lappie to kernel 2.6.24.22 this morning.  Broadcom BCM4311 is working like a dream on the wl driver and wicd is BEAUTIFUL!

suspend works great - tested a couple of times.

Now just have to get it to behave when suspending by closing lid - but right now I'm just so happy that resume is working great!

---

