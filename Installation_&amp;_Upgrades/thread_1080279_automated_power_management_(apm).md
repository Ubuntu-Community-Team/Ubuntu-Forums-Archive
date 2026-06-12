---
title: "automated power management (apm)"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by lalawawa on 2009-02-25
I want my computer to go into 'suspend' mode when unused for any length of time.  When I was on version 7 (Feisty Fawn) this worked.  I upgraded to 8 and it goes into suspend mode, but won't come back without a reboot.  I looked up automatic power management (apm) in the Synaptic Package Manager, and it says apm defaults to off.  To turn it on, I have to specify apm=on to the command line for booting from lilo.  However, lilo is not installed on my system, grub is.  How do I tell grub to enable automatic power management when I boot my machine, or better still, how do I get a working 'suspend' mode on my machine?

---

### Post by lalawawa on 2009-02-27
This is really bad that apm defaults to off on Ubuntu 8.04.  That means when unused my computer is consuming about 60 watts while in sleep mode it would be only about 3 watts.
    I have two computers, a Windoze box and an Ubuntu box.  The Windoze box has automated power management and goes to sleep when you leave it alone for a few minutes, and wakes up VERY quickly when you wave the mouse around.
    I really want to do my bit for the planet and save energy, but I'm not willing to power down my computer every time I walk away from it for a few minutes, and have to reboot every time I want to use it again.  I'm willing to go to a different distro if I have to for this feature.  Or maybe go back to Fiesty Fawn.  Please somebody help me get apm turned on.

---

### Post by oldos2er on 2009-02-27
There are some suggestions here: [http://ubuntuforums.org/archive/index.php/t-2620.html](http://ubuntuforums.org/archive/index.php/t-2620.html)

---

### Post by khelben1979 on 2009-02-27
Why not create a small script for this and place it in the /etc/init.d/ directory?

Also [this link]("http://wiki.osdev.org/APM") might be interesting to you.

---

### Post by lalawawa on 2009-03-01
Thanks for the help.  I managed to get apm installed, but it did not solve my problem.
    When I did System->Quit, "suspend" was no longer an option.  I set Preferences->Screensaver->Power Management to put the computer to sleep, but as before, I couldn't wake it up again without rebooting.  I still don't understand how to get an Ubuntu box to go to sleep when it's not in use in such a way that it will wake up appropriately.

---

