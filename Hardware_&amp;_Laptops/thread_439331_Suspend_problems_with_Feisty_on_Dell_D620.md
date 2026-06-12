---
title: "Suspend problems with Feisty on Dell D620"
date: 2007-05-10
forum: Hardware &amp; Laptops
---

### Post by charles.figura on 2007-05-10
I've just fairly successfully installed feisty on my D620 (with Intel 945GM video, 1440x900 LCD, Intel 3945 wireless).  Installation has gone without a hitch EXCEPT for ACPI.

When I try to suspend, the suspend shut-down seems to take a longer time than normal, and the system does not wake up successfully (ever, to the extent that I've tested).   I've gotten a variety of resume behaviors:
- system hangs with blank screen, num- and alpha-lock lights flash, no response
- display flashes/clears, backlight is on, num- and alpha-lock lights respond, but display is blank.  system will shutdown in response to pressed power button.
- system just hangs with blank screen, no backlight, no nothing.

Suspend worked on this machine quite well under both Dapper and Edgy - I'm a bit suprised that it's not working under Feisty.  Anyone have any ideas?

---

### Post by odix on 2007-05-10
Same for me too, same machine, except for NVIDIA graphics, works perfectly in edgy, but not in feisty
Do you have any experience with hibernate (suspend to disk) ?

regards odi

---

### Post by charles.figura on 2007-05-10
Um, yeah.  Won't do it.  I get a 'KDE could not launch suspend: could not find suspend executable.' popup.
Is there a package that I've forgotten to install?  I don't remember that I had to install something extra.  

Do I need the 'hibernate' or 'suspend2' packages?  I'm a bit perplexed - I don't remember installing them before, and logic suggests that hibernation/suspension should be automatic, not an optional package.

-C

---

### Post by Immolatus on 2007-05-11
Me too with the suspend stuff. I keep finding that people are blaming this problem on video drivers but I don't see the correlation. I'm running the integrated intel chipset as well and have the same problems. Suspend only once and not come back from it just POOF! off it goes.
However I can tell you that the blinking NUMLOCK or CAPSLOCK mean "kernel panic", which I have also been experiencing with feisty:(. But I've narrowed that down to the desktop effects.
If I turn them off it doesn't happen.

---

### Post by charles.figura on 2007-05-11
Hibernation Update -

My system will hibernate when using the hibernate function from either the system tray logoff button or from the system tray acpi control.  Hibernate does *not* work using the Fn-F1 hotkey combination - that's when I get the KDE popup error mentioned above.

---

### Post by Immolatus on 2007-05-12
All methods act the same for me.

---

### Post by strabes on 2007-05-12
This page might shed some light: [http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200](http://www.thinkwiki.org/wiki/ATI_Mobility_FireGL_V5200)

Check out the "Proprietary ATI driver on Ubuntu Feisty" part. Part 3 is what ended up fixing it for me.

---

### Post by charles.figura on 2007-05-12
Alex -

The thinkwiki.org approach is similar to that from the D620 laptop testing page - [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620) .
The suspend solution there is listed for Dapper & Edgy (and worked for me for both of them.  For Feisty, results are mixed (and unacceptable) - tried suspending four times in a row with the following results:
- kernel panic on resume (no display)
- backlight on, no display, keyboard response (power button shutdown)
- 'proper' resume!  Yay!  Wireless came back, everything looks shiny
- looks like a proper resume, but no keyboard/touchpad.  Can't do dip.
Further attempts typically give (bad) results, usually one of the no display options.
I've only got a successful resume that once.

---

### Post by odix on 2007-05-23
New News:
It seems that it depends on the propritary nvidia drivers, at least on my machine. I've installed the nvidia_glx_new and suspend doesn't work, the machine suspends but crashes after wakeup. Tried with the nv (open source) drivers, suspend and wakeup works perfectly, not tried the "standard" nvidia_glx, because after installation of nvida_glx_new it's not possible to initialize the nvidia kernel driver (API missmatch).

regards odiX

---

### Post by sgarman on 2007-05-25
I have a new (month old) Latitude D620 and suspend and hibernate are now working flawlessly. It has the following specs:

2.0 GHz Core2Duo
2 GB RAM
120 GB 5400 RPM Hard Drive
Intel 945 Graphics
WXGA+ 1440x900 LCD Resolution
Intel 3945 Wifi
No Bluetooth/No fingerprint reader.

After doing a fresh install of Fiesty, I had to install the 915resolution package and reconfigure Xorg using it. Then I made changes to my ACPI config according to this page:

[https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD620)

At that point suspend worked most of the time, but I was having issues on wakeup where my keyboard and trackpad stopped working. That led me to start the following thread, which toward the end has a solution that now gives me perfectly reliable suspend:

[http://ubuntuforums.org/showthread.php?t=437596](http://ubuntuforums.org/showthread.php?t=437596)

I would be happy to share any configuration files with you to help resolve your issues, if you're running the same hardware config, just ask.

Regards,

Scott

---

### Post by charles.figura on 2007-05-25
Scott -

Brilliant.  I'd been following the keyboard/mouse freezeup thread you linked, but hadn't gotten the chance to try it out.  I saw some flukey behavior the first time or two I suspended AFTER applying the patch, including:

on resume:
black screen, pointer appears, can move it for about 2 seconds
pointer freezes for about 2 seconds
pointer disappears for about 2 seconds
cycle repeats - no display, just black screen.  Have to reboot to get out (seen this before...)

Once when I told it to sleep, the heartbeat light indicated it had gong to sleep, but screen stayed ON - weird dark green glow.  I was waiting for Mulder & Scully to show up.  When it resumed, seemed okay, though...

Since then, I've done about 8 or so suspend/resume cycles with no ill effects.

---

### Post by xadder on 2007-05-25
Just info. suspend used to work on my machine (IBM Thinkpad), but started behaving oddly after a recent update. Others are having similar problems (search for suspend on forum), and bugs have been posted to launchpad. Hopefully Ubuntu will fix this soon with a nice simple update. (Many Ubuntu problems seem to go away if one is patient, although occassionally new ones are introduced!)

---

### Post by DouglasK on 2007-05-30
The instructions for Suspending and Resuming the Dell lattitude 620 worked on a Dell inspiron 8500 perfectly.  [https://wiki.ubuntu.com/LaptopTestin...llLatitudeD620](https://wiki.ubuntu.com/LaptopTestin...llLatitudeD620)

Thanks a million to all in this thread.

---

### Post by charles.figura on 2007-06-06
Well, it looks like I was a bit premature.  I'm getting one suspend/resume cycle (typically) working, then the second fails in a variety of ways and requires a powercycle.

Hibernation still works well, though interestingly enough, the hibernate hotkey ONLY works the first time after a fresh boot - it's not recognized (doesn't even register on xev) after that.

It sounds like others out there are having good luck with suspend on the D620.  I'm tempted to try a fresh install.

---

