---
title: "[SOLVED] screen blanking when I don't want it to"
date: 2008-10-14
forum: General Help
---

### Post by eilenbeb on 2008-10-14
...just like a 'blank screen' screensaver.
After a little bit of inactivity, my screen blanks out.

Trouble is, I haven't installed any screensaver support (that I know of).

I'm running a barebones install:
ubuntu-minimal
xorg
icewm
nvidia-glx-new
xdm
and a few lightweight tools/utilities

I also haven't installed any power managers (except acpi and acpid, of course).  I've also turned off everything I could in my Award bios.

I have a full Gnome install on another drive with screensavers turned off, and powersaving set to 'never'.  I have the same problem in this system.

When the screen blanks out, any program that is doing a download dies.
This makes me think it's a power management problem.  My ethernet device might be getting turned off at the same time, causing the crash.

This screen blanking does not happen in windows.

So, I have 3 basic questions:
Is there some setting in Linux that could solve this problem?
Is there a way to override the bios power settings?  (in case it's the bios's fault)
Is there any chance it could actually be a screensaver feature?

Thanks,
b

---

### Post by Yellow Pasque on 2008-10-14
Your screen is probably blanking because of DPMS.
```
gksudo gedit /etc/X11/xorg.conf
```
Add a Serverflags Section (or add the Options if one exists)
```
Section "ServerFlags"
        Option       "BlankTime"        "0"
        Option       "StandbyTime"      "0"
        Option       "SuspendTime"      "0"
        Option       "OffTime"          "0"
        Option       "NoPM"             "true"
EndSection
```

Does that help?

---

### Post by eilenbeb on 2008-10-14
Thank you.  Seems to have worked.
I'll need to do a large download to be sure, but so far so good.

My system fans seemed to run heavy, so I set "NoPM" to "false" and everything seems ok.

laters,
b

---

