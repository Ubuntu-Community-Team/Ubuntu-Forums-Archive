---
title: "Anyone has luck with suspending Dell E1505 laptop with ATI graphics?"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by garion on 2007-04-21
I have a Dell E1505/6400 laptop with ATI x1300 video running fglrx.  Suspend used to work fine on Edgy and Feisty beta (with the tweak of changing POST_VIDEO to false in acpi-support), but it was broken with a recent kernel update shortly before the final release (suspend is okay but blank screen after resume).

Has anyone had luck with this particular line of Dell laptops (E1405, 1505, 1705)?  Thanks.

---

### Post by odelay on 2007-04-21
I have the same setup as you.  Suspend worked perfectly in Edgy...but I just get stuck with a blank screen and have to force restart with Feisty.  This is a HUGE issue for me...since I'm constantly moving from one class/area to another and absolutely need to be able to suspend the computer.

---

### Post by mitcha on 2007-04-21
My laptop is 6400 with x1400 and I had solved the problem like this :
1. download a xorg-driver-fglrx deb file from any ubuntu mirror website,the file I download  is xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-15.20_i386.deb
2. put the file in a fat32 or ntfs partition so that it can be mouted in linux
3. boot the livecd ,hen the screen goes blank, switch to a virtual console,mount the partition and run the deb file and run some command ,then  restart x, done!
[I]sudo dpkg -i xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-15.20_i386.deb
sudo aticonfig --initial
startx[/I]

It really worked in my laptop and maybe usefull for some dell 6400/1505 users with ATI card,hope this would help you

---

### Post by garion on 2007-04-21
hmmm... sorry if i am being dense... i don't really get this.  are you describing your way of installing fglrx driver?  i am not sure how that is related to the suspending issue, maybe you can explain a bit more?




> **mitcha said:**
> My laptop is 6400 with x1400 and I had solved the problem like this :
1. download a xorg-driver-fglrx deb file from any ubuntu mirror website,the file I download  is xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-15.20_i386.deb
2. put the file in a fat32 or ntfs partition so that it can be mouted in linux
3. boot the livecd ,hen the screen goes blank, switch to a virtual console,mount the partition and run the deb file and run some command ,then  restart x, done!
[I]sudo dpkg -i xorg-driver-fglrx_7.1.0-8.34.8+2.6.20.5-15.20_i386.deb
sudo aticonfig --initial
startx[/I]

It really worked in my laptop and maybe usefull for some dell 6400/1505 users with ATI card,hope this would help you

---

### Post by mitcha on 2007-04-21
Embarrassing......I made a mistake

---

### Post by legzelda on 2007-04-21
I can suspend my E1505 running Feisty if I logout, restart X (Ctrl + Alt + Backspace), then select suspend without logging in.  This has worked without fail for the past few days.  I can sometimes get the laptop to suspend when running a standard Gnome session, or even an Xgl session so I can use Beryl, but it freezes my computer more often than not.

If it helps, here is my /etc/default/acpi-support:
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
USE_DPMS=false

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
#LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql bluetooth"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

---

### Post by odelay on 2007-04-21
Hey...I found a fix.  I didn't have to reinstall any drivers...just change four simple lines in the acpi config file.  Took 2 seconds and suspend/resume works great for my Dell e1505/ATI x1400.

Just follow the instructions given in this thread:

[http://ubuntuforums.org/showthread.php?p=2501595#post2501595]("http://ubuntuforums.org/showthread.php?p=2501595#post2501595")

Hope that helps

---

### Post by garion on 2007-04-21
hmm :(  didn't work for me, don't know why, still stuck with a blank screen on resume.  i've tried it with 8.34 fglrx in repo, 8.35 installed with envy, 8.36 installed manually, same thing.  here is my acpi-support.  odelay, how is mine different from yours?  maybe you can show me your xorg.conf as well?

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
# LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql bluetooth"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

```




> **odelay said:**
> Hey...I found a fix.  I didn't have to reinstall any drivers...just change four simple lines in the acpi config file.  Took 2 seconds and suspend/resume works great for my Dell e1505/ATI x1400.

Just follow the instructions given in this thread:

[http://ubuntuforums.org/showthread.php?p=2501595#post2501595]("http://ubuntuforums.org/showthread.php?p=2501595#post2501595")

Hope that helps

---

### Post by legzelda on 2007-04-21
Hi again!  I have been testing my system, and it has successfully suspended while signed in (including the Xgl session so Beryl will work).  If it helps anyone, here is my /etc/default/acpi-support:

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
USE_DPMS=false

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
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql bluetooth ndiswrapper"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

---

### Post by garion on 2007-04-21
hmm... pretty much the same as mine, but mine doesn't work... what exact hardware do you have?




> **legzelda said:**
> Hi again!  I have been testing my system, and it has successfully suspended while signed in (including the Xgl session so Beryl will work).  If it helps anyone, here is my /etc/default/acpi-support:

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
USE_DPMS=false

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
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql bluetooth ndiswrapper"

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false
```

---

### Post by odelay on 2007-04-21
Are you guys that can't get it to work using the ATI drivers or the xorg fglrx drivers?  I'm using the latter, and it seems like the fix I tried applies solely to fglrx.  Just a thought.

---

### Post by garion on 2007-04-21
I am using fglrx driver, like I said I've tried the one in the repo 8.34, and also 8.35 and 8.36... none of them works.  I don't know what monitor resolution you have on your E1505, because mine is 1680x1050 and this won't work unless I install the fglrx driver.

With the beta Feisty, I didn't have to do anything except changing POST_VIDEO to false.  Now I tried a multitude of combinations of option changes in acpi-support, and none works :(.  I don't think I installed anything special either... does your acpi-support looks EXACTLY the same as mine?  If not, please let me know the differences if you don't mind.

For the xorg.conf, I basically just used the original file, ran "aticonfig --initial", "aticonfig --overlay-type=Xv", and "aticonfig --resolution=0,1680x1050", and finally added a section to disable "Composite", that's it.  Didn't do anything strange manually.  Is there something different you did with your fglrx installation?

Thanks :)




> **odelay said:**
> Are you guys that can't get it to work using the ATI drivers or the xorg fglrx drivers?  I'm using the latter, and it seems like the fix I tried applies solely to fglrx.  Just a thought.

---

### Post by legzelda on 2007-04-21
I am using a Dell E1505 running Feisty using the fglrx drivers (8.35.5).  I have an Intel Core 2 Duo @ 2GHz and 1GB of RAM.  I have internal Bluetooth, as well as wireless running through ndiswrapper.  Does that help at all?  I'm not sure what other relevant hardware specs might make a difference.

> **garion said:**
> hmm... pretty much the same as mine, but mine doesn't work... what exact hardware do you have?

---

### Post by garion on 2007-04-22
Hmm... is your video card x1300 or x1400?  Seems like those two tend to behave differently with suspending usually, not sure why though since they are more or less similar.  I am using an Intel wireless 3945abg card, which is supported with open source driver out of box.  But my gut feeling is that it's the video that's creating the problem... not sure what's happening in my case though *scratching my head* :confused: 



> **legzelda said:**
> I am using a Dell E1505 running Feisty using the fglrx drivers (8.35.5).  I have an Intel Core 2 Duo @ 2GHz and 1GB of RAM.  I have internal Bluetooth, as well as wireless running through ndiswrapper.  Does that help at all?  I'm not sure what other relevant hardware specs might make a difference.

---

### Post by legzelda on 2007-04-22
I have an X1400 -- duh!  I'm sorry I forgot to include the video card.  That was pretty forgetful of me.  Yes, it seems like it's the video card causing our problems, not the wireless card, because when I suspended my computer without the fglrx drivers installed, it suspended without any problems--the only problems I encountered happened after I installed the drivers.  However, I found adding ndiswrapper (for my wireless) to the STOP_SERVICES section of /etc/default/acpi-support seemed to help.  Seeming as your card is more supported, however, I would assume you don't even need to worry about it.

---

### Post by garion on 2007-04-23
yah, this is truly annoying... everything i tried left me with a blank screen with no response to keyboard whatsoever.  because i carry my laptop everywhere, i just can't live without suspend working... which means i had to stick with windows or maybe another distro on my laptop if this can't be fixed... :(




> **legzelda said:**
> I have an X1400 -- duh!  I'm sorry I forgot to include the video card.  That was pretty forgetful of me.  Yes, it seems like it's the video card causing our problems, not the wireless card, because when I suspended my computer without the fglrx drivers installed, it suspended without any problems--the only problems I encountered happened after I installed the drivers.  However, I found adding ndiswrapper (for my wireless) to the STOP_SERVICES section of /etc/default/acpi-support seemed to help.  Seeming as your card is more supported, however, I would assume you don't even need to worry about it.

---

### Post by garion on 2007-04-23
I realized that my problem could be more than just video, because apparently the keyboard freezes on resume (i.e. even the capslock doesn't work), and that's probably a sign of conflict with the framebuffer.  So I used vga=0 to boot the kernel, and indeed that solves the keyboard issue, capslock is working.  BUT yet no luck with the black screen with all kinds of acpi-support settings.

Another thing I tried is to use s2ram to suspend instead (also with vga=0), and that seems to bring the screen back too (with -f -a1 or -f -p -m, both seem to behave similarly).  However, I got a console with error messages, showing the I/O to the hard drive seems to be dead, and there is no access to the file system.  Reboot/shutdown commands obviously don't work either, so I still had to push power button to hard reboot.  I tried s2ram under console with the rescue kernel too, same issue, keyboard and screen back but no file system access.

Unfortunately, by now I've probably hard shutdown my laptop over 50 times trying different things... I figure that if keep trying this insane stuff I will perhaps kill my computer before anything works.  I am giving up for now, but if anyone here has suggestion of something different to try, please do let me know :)

A little bit off-topic, this is honestly *really really* frustrating... Feisty is very nice, I love it otherwise, but this single problem messed up the entire mobile usability.  Come to think of it, even if I can somehow get it to work with some subtle workaround, chances are the next kernel update is going to crap it up again.  Then what?  I need to google for hours online and hard boot my computer for another 50 times?  I admit that this is only the second time I tried to run linux as primary os on a laptop, last time years ago with Ubuntu 4.10 when nothing worked out-of-box, and a few things never worked.  There is definitely a lot of progress, but it appears like I am inching towards another failing attempt :lolflag:, on something windows users have taken for granted to work flawlessly for many many years...

---

### Post by legzelda on 2007-04-24
Although I see your point and have been, at times, very frustrated with Linux in general and Ubuntu in particular, we have to remember we're dealing with free, open-source software.  And, our problem is probably the video card, which means we can blame ATI and its lackluster Linux support.  My girlfriend uses Ubuntu with her nVIDIA card, and everything works without any problems.  Indeed, I was very jealous, but such is the Linux life.

As far as your keyboard not working, I suppose it's all a part of the xorg.conf file.  If you run dpkg-reconfigure xserver-xorg and reset everything to default (thus replacing the xorg.conf with your properly working ATI drivers), you will get a system without 3D support, but you shouldn't have any problems getting suspend mode to work.  For me, it was only after I installed the ATI drivers that I ran into problems.

At any rate, good luck finding a solution to your problem.

> **garion said:**
> I realized that my problem could be more than just video, because apparently the keyboard freezes on resume (i.e. even the capslock doesn't work), and that's probably a sign of conflict with the framebuffer.  So I used vga=0 to boot the kernel, and indeed that solves the keyboard issue, capslock is working.  BUT yet no luck with the black screen with all kinds of acpi-support settings.

Another thing I tried is to use s2ram to suspend instead (also with vga=0), and that seems to bring the screen back too (with -f -a1 or -f -p -m, both seem to behave similarly).  However, I got a console with error messages, showing the I/O to the hard drive seems to be dead, and there is no access to the file system.  Reboot/shutdown commands obviously don't work either, so I still had to push power button to hard reboot.  I tried s2ram under console with the rescue kernel too, same issue, keyboard and screen back but no file system access.

Unfortunately, by now I've probably hard shutdown my laptop over 50 times trying different things... I figure that if keep trying this insane stuff I will perhaps kill my computer before anything works.  I am giving up for now, but if anyone here has suggestion of something different to try, please do let me know :)

A little bit off-topic, this is honestly *really really* frustrating... Feisty is very nice, I love it otherwise, but this single problem messed up the entire mobile usability.  Come to think of it, even if I can somehow get it to work with some subtle workaround, chances are the next kernel update is going to crap it up again.  Then what?  I need to google for hours online and hard boot my computer for another 50 times?  I admit that this is only the second time I tried to run linux as primary os on a laptop, last time years ago with Ubuntu 4.10 when nothing worked out-of-box, and a few things never worked.  There is definitely a lot of progress, but it appears like I am inching towards another failing attempt :lolflag:, on something windows users have taken for granted to work flawlessly for many many years...

---

