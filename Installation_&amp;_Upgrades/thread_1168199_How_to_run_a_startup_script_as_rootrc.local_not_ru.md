---
title: "How to run a startup script as root/rc.local not running"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by Richardcavell on 2009-05-23
Hi,

I'm using Ubuntu 9.04 on the third partition of my Intel Macbook2,1.  I want to run the following command *as root* every time Ubuntu loads:

xrandr --output LVDS --set BACKLIGHT_CONTROL combination

This command fixes the backlight brightness controls for Macbooks.  It doesn't work if it's not root.  If I type 'sudo' plus the command within a terminal, it works perfectly.  But I want it to run automatically.

So I tried this: My /etc/rc.local now reads as follows:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

xrandr --output LVDS --set BACKLIGHT_CONTROL combination
firefox

exit 0

I put the 'firefox' line in there just to test if this script is running at all.  ls -l /etc/rc.local yields:

-rwxr-xr-x 1 root root 372 2009-05-24 10:20 /etc/rc.local

Upon booting, the brightness controls are not fixed, and firefox does not load.  What's wrong?

TIA,

Richard

---

### Post by Brandon Williams on 2009-05-23
I don't think that either xrandr or firefox will run from rc.local, because rc.local is not run in an X environment. I recommend that you add the xrandr call to the list of applications that are run when you login. If xrandr needs to be run as root, then you can launch it with gksudo.

---

### Post by Aearenda on 2009-05-23
Brandon is right. In addition, you could set sudo so that your 'sudo xrandr' call does not require a password, using 'sudo visudo' and adding a line like this at the end:```
fred ALL=NOPASSWD: /full/path/to/your/command
```
Obviously you need to put your username and the proper path to the command in there. If you create a local file to contain the xrandr command, make sure it is only writable by root to avoid creating a security hole.

---

### Post by Richardcavell on 2009-05-23
Thank you.  Now, how do I make it run on login?

I have found System->Preferences->Startup Applications and I have added an item in 'Startup Programs' that contains the command:

gksudo xrandr --output LVDS --set BACKLIGHT_CONTROL combination

I have also tried 'sudo' instead of 'gksudo', and without the 'sudo', and I even tried putting the command in a script.

But it doesn't have the desired effect.

Richard

---

### Post by Aearenda on 2009-05-24
Are you absolutely sure you need it to run as root? I have a call to xrandr in one of my login startup entries, and it works fine. Make sure the no password workaround is in place properly.

Anyway if you look in ~/.xsession-errors it might give you a clue somewhere. This is where startup program output goes.

---

### Post by Richardcavell on 2009-05-24
Hi, Thanks to both who replied.

I'll post the outcome here for future reference.  It turns out that it doesn't need sudo at all, and it seems that sudo/gksudo was what was stopping it from functioning correctly (since it didn't have a password and had no command line interface with which to obtain one).  In 9.04, I use System->Preferences->Startup Applications, and simply paste the command with all its switches, and it works.

Richard

---

### Post by Aearenda on 2009-05-24
That's good news, thanks for telling us the outcome!

---

