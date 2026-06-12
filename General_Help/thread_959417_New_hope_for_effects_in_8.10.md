---
title: "New hope for effects in 8.10"
date: 2008-10-26
forum: General Help
---

### Post by CarnivorouZ on 2008-10-26
The ATI drivers have crashed my system since every build since 7.10 when i started using Ubuntu; that is until now.  The proprietary driver located in Hardware Drivers worked without a glitch and I could restart without a white screen.  
I am still unable to enable effects however and here is the outputs I get:

```
chase@chase-linux:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon X1650 Pro (rev 9e)
 Driver in use:         fglrx
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 
```

---

### Post by CarnivorouZ on 2008-10-26
```
chase@chase-linux:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  160 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
```

---

### Post by CarnivorouZ on 2008-10-26
bump

---

### Post by Alpha-geek on 2008-10-26
I have an ATI HD3870. I used Envy NG to install the drivers & all worked perfectly.

---

### Post by CarnivorouZ on 2008-10-27
Just tried it with Envy but it has a new look to it now and wont let me install over drivers that it sees as correct.  So I have a checkmark on Enabled for my ATI driver but still no desktop effects.

---

### Post by Safder on 2008-11-05
I recently upgraded to the Ubuntu 8.10, and struggled with the effects...for the last two days, the reason being, i couldn't install all the files, during upgrading, but I manually installed those files, once that was done, my effects started working and as for running compiz-check, the result was the same for me as you posted in your first spot, even after my desktop effects started working. The following is a link to some of the problems I faced, maybe you can get some pointers
[http://ubuntuforums.org/showthread.php?t=967317](http://ubuntuforums.org/showthread.php?t=967317)

Good luck ! ! !

---

