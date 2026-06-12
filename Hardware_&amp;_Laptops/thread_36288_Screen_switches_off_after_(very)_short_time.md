---
title: "Screen switches off after (very) short time"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by g_crawford on 2005-05-22
I just installed Ubuntu on my fairly low spec Dell a couple of days ago, and after only a couple of minutes my screen switches off.  This isn't a huge problem, I just want it to take a bit longer before it does that.  My Screen saver is set to come on after 5 minutes, but it doesn't even get a chance!  Where can I change the settings for my laptop?

Also, in Ubuntu is it a bad thing to just press the power button and have it switch off instantly?  I just hate having to wait for it to shut down before shutting the laptop itself.  I'm pretty new to laptops, so maybe I can just shut the laptop while Ubuntu shuts down lol, I don't even know.

I'd appreciate any help, Thanks guys. :-)

---

### Post by 23meg on 2005-05-22
check if you have monitor power management enabled in system / preferences / screensaver / advanced / display power management and readjust the values if they're set too low. if just pressing the power button once turns off your laptop instantly (this means you're not using ACPI), don't do it. if it initiates the regular linux shutdown procedure, it's ok. in any case, you'll have to wait for the shutdown procedure to finish for a safe shutdown.

---

### Post by g_crawford on 2005-05-22
is there anywhere i can set the power button to start the shutdown?  I would look, but I'm at work at the mo, taking notes for when I get home :-)

---

### Post by 23meg on 2005-05-22
if it's a very old laptop it may not have ACPI support. if it had it, chances are ubuntu would have configured things so that the power button would shut down your computer the ACPI way. anyway, if you're 100% sure it has ACPI, modify your /etc/acpi/powerbtn.sh file to look like this if it does not already:

```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

if ps -Af | grep -q '[k]desktop' && test -f /usr/bin/dcop
then
    dcop --all-sessions --all-users ksmserver ksmserver logout 0 2 0 && exit 0
else
    /sbin/shutdown -h now "Power button pressed"
fi

```

---

