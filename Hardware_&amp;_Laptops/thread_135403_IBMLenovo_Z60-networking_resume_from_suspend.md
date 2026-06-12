---
title: "IBM/Lenovo Z60-networking resume from suspend"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by LittleLebowski on 2006-02-23
Hello, I'm running Kubuntu/Ubuntu on my beautiful new Z60m.  Works flawlessly but for 2 things:

  -suspend seems to limited to which DE (GHome/KDE) I'm using.  Is there a way to make this DE independent?  

  -I ahve to restart networking manually every time I resume from suspend.  Any way to do this automagically?

  Other than that, this is a wonderful distribution.  Good job, Ubuntu/Kubuntu team!  Everything JUST works.

---

### Post by pestilence4hr on 2006-02-23
Yes, you should edit files in /etc/acpi.  I have the power button on my laptop initiate suspend, that is DE independent.  It's /etc/acpi/powerbtn.sh, and i have in it calling  /etc/acpi/sleep.sh

You can also edit these scripts to take any arbitrary action you would like.  Perhaps you need to unload/reload your networking modules on suspend/resume?  In any event, if you know what action to take that restores networking, just put it in /etc/acpi/resume.sh

---

