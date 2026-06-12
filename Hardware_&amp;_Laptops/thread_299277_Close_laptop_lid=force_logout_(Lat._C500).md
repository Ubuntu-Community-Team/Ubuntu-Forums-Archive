---
title: "Close laptop lid=force logout? (Lat. C500)"
date: 2006-11-13
forum: Hardware &amp; Laptops
---

### Post by ignavia on 2006-11-13
I'm running Edgy on a Latitude C500, and when I close the lid, I get forcibly logged out. When I open it again, I'm at the GDM screen as if I had just booted up. This occurs regardless of the power settings: I've had the 'when I close laptop lid' set to 'blank screen' and 'do nothing', but it still kicks me out every time. I've also tried changing CMOS settings to no avail.

This same machine used to run Dapper just fine.

What can I try?

---

### Post by ignavia on 2006-11-14
For those who find this thread by searching, here's what worked for me:

From the thread [http://www.ubuntuforums.org/showthread.php?t=284872](http://www.ubuntuforums.org/showthread.php?t=284872) (modified)

Add the following to the bottom of your /etc/X11/gdm/gdm.conf-custom

```

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 -noacpi

```

The original thread states to edit the gdm.conf file, but the file explicitly states not to edit it, that the -custom file will overwrite any settings, so I added the lines there.

---

### Post by tvst on 2006-11-17
I'm having the same problem and will try your solution. 
Does anyone know what the consequences of running 'noacpi' is? What does one miss if X does not listen to ACPI events?

---

