---
title: "Custom suspend utility: best practice in Maverick"
date: 2010-11-27
forum: Hardware
---

### Post by dsjstc on 2010-11-27
I'm running Maverick on a Portege 3500.  Everything's great except suspend, which I cannot seem to make work except with "acpitool -s".

I'd like to modify the suspend scripts to use that utility.  Is there a single suspend hook that I can override, or do I need to modify the button handlers directly?

Alternately, is there documentation somewhere explaining the architectural thinking behind the ACPI scripts?

---

### Post by meijer.o on 2010-11-27
Dear linux user,

replace the following file (symbolic link) with this script:
login as root: 

sudo -i
mv /usr/sbin/pm-suspend /usr/sbin/pm-suspend.bak
gedit /usr/sbin/pm-suspend

and type in gedit:

#!/bin/sh
#
acpitool -s

save file and exit gedit

make /usr/sbin/pm-suspend executable

chmod +x /usr/sbin/pm-suspend

This works fine for me. Let me know if it does not work, kind regards, Otto Meijer

---

### Post by kerry_s on 2010-11-27
gksudo gedit /etc/acpi/sleep.sh

change "pm-suspend" to your command

there's also 1 for the button & lid if you use those.

---

### Post by dsjstc on 2010-11-28
Thanks Kerry, I spent a couple of hours playing with /etc/acpi/lid.sh and sleep.sh, but I could not prevent it from irretrievably disabling networking and switching to (blank) VT8 on resume.

Ultimately I gave up and went with Otto's hack.  Replacing /usr/sbin/pm-suspend had exactly the desired effect, after I set SUSPEND_METHODS="pm-utils" in /etc/default-acpi-support.

Thank you both for your suggestions.

---

