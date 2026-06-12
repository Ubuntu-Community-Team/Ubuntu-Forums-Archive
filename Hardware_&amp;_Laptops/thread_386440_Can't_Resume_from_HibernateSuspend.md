---
title: "Can't Resume from Hibernate/Suspend"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by DocHoliday52090 on 2007-03-17
HP nc6220 won't resume from Hibernate or Suspend. It did once, but it stopped after either an update or when I fixed the wireless. 

Or that might just be a coincidence. 

There is a black screen, and the mouse appears. The mouse is normal for some time before the loading icon appears. Then the mouse disappears. Then it appears some time later. This keeps on happening until a cursor (or something similar) comes up in the top left corner. 

I've tried added 'nm-applet' to the STOP-SERVICES list in /etc/defaults/acpi-support, but that doesn't seem to work:

[QUOTE=etc/defaults/acpi-support]# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES="mysql "
nm-applet[/QUOTE]

I'm not sure if the syntax is correct either. 

Any help is appreciated.

---

### Post by casaschi on 2007-03-17
the correct syntax is
STOP_SERVICES="mysql nm-applet"

to debug the resume process, try CTRL-ALT-BACKSPACE at the end of the resume.
For some people, restarting the X server with CTRL-ALT-BACKSPACE works and brings you to a login screen. This shows you might have to fix something in your video config.
Alternatively, open a console login with CTRL-ALT-F1 and look at logfiles...

---

