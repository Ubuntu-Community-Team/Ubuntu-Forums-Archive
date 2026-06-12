---
title: "How can I change the monitor that the login screen appears on in 18.04?"
date: 2018-07-31
forum: Hardware
---

### Post by bofh19612 on 2018-07-31
I have a TV attached to the HDMI port and a monitor on the DVI port.  When I booted up in 16.04 the login prompt moved to whichever screen had the mouse cursor in it, which was convenient as the TV is usually switched off or in use by someone else.  Since upgrading to 18.04 the login screen only appears on the TV.  After logging in I can go to settings, displays where the TV shows up as display 1 and the monitor as display 2.  I guess I need to reverse that in a configuration file somewhere.

---

### Post by QIII on 2018-07-31
Hello!

The numbers are somewhat arbitrary and are assigned during startup as the kernel queries the hardware.  The GPU is no doubt reporting the ports with those numbers and that will be done consistently by the firmware.  That numeric assignment is not really the issue.

I assume you are using vanilla Ubuntu. It has been some time since I used a GNOME DE regularly, but I believe the display settings should allow you to set one or the other of the "monitors" as primary.  That should place your greeter on that screen.

Let us know if that works or not.

KDE presents the greeter on all three of my monitors and I need to be sure to use the "primary" monitor to log in or the screens get switched around on me when the DE starts.  Annoying, but that's how it is.  :)

Cheers!

---

### Post by bofh19612 on 2018-07-31
The display settings only affect which display becomes primary after login - they are user specific.  Every time I've booted in 18.04 the login has appeared on the HDMI output and display 1 is always on there.  It might be arbitrary but, if it is, then it's very consistent.

---

### Post by QIII on 2018-07-31
> they are user specific

Ah.  Right indeed.  

I may need to boot to a GNOME installation later and see what can be done.  I suspect that somewhere in /etc there is a DM config file that has a setting for which screen is active at startup.  That might be useful.  I would expect that the DM config directory would be directly under /etc and easy to find.

---

### Post by bofh19612 on 2018-07-31
I've found a gdm3 directoiry under etc...  is that the fella?

---

### Post by QIII on 2018-07-31
Likely.

Do you see any *.conf files there?

---

### Post by bofh19612 on 2018-07-31
custom.conf  and folders called init, postlogin, postsession, presession, prime and primeoff

custom.conf text;

# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

# Enabling automatic login
#  AutomaticLoginEnable = true
#  AutomaticLogin = user1

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

[security]

[xdmcp]

[chooser]

[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true

---

### Post by QIII on 2018-07-31
Unfortunately I don't want to take swing in the dark.  I'm on my cell phone, peeking in from time to time when I am waiting for some regression tests to complete.  The client I am at today is a Windows shop (Yes, I am a mercenary. I make contracts where the money is!).  Not sure why I test my work, since it is always perfect!  :)

Armed with the information you have provided, let's hope someone else can step in with more details.  I'll likely be here for the rest of the day.

---

### Post by bofh19612 on 2018-07-31
There is a lightdm folder under etc as well...

---

### Post by bofh19612 on 2018-07-31
I uncommented the "#WaylandEnable=false" line and it now defaults to the PC monitor as I wanted.  As a bonus, Firefox now loads quicker and without looking quite so messy.  Thanks very much for pointing me in the right direction.

---

### Post by QIII on 2018-07-31
Glad you gave me the opportunity to learn something new!

Hope you had made a backup before you started making changes in case something blew up.

I often think of /etc as "Everything To Configure" ... system-wide, that is.  Back in the day, it was really what it sounds like.  "etc".  It was a catch-all for everything nobody knew where else to put things.

---

### Post by bofh19612 on 2018-07-31
I keep my data on a hard drive and the system on an ssd so I didn't bother backing up.  The Wayland line just didn't look right - I was sure that I'd read somewhere that 18.04 had rejected Wayland for X.  I must have been using Wayland with 16.04 so the online upgrade kept it there.  Extra bonus, the firewall gui started working again as well.  It hadn't since the upgrade.

---

### Post by QIII on 2018-07-31
Bonus!

---

