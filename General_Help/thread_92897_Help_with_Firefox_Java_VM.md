---
title: "Help with Firefox Java VM"
date: 2005-11-20
forum: General Help
---

### Post by Bachstelze on 2005-11-20
When I try to view a Java applet on Firefox, it crashes at the end of loaing the applet and I get this in the terminal : 

```
#
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1e39d03, pid=18362, tid=2978892720
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_05-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ed03]
#
# An error report file with more information is saved as hs_err_pid18362.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
INTERNAL ERROR on Browser End: Pipe closed during read? State may be corrupt
System error?:: Success
```

Any ideas ? Perhaps my VM is f***ed up or baly installed. This is the first time I tried it. I downloaded it with Automatix.

---

### Post by jliedeka on 2005-11-20
Try running:

update-alternatives --list java

It may be that gij is your default and you have to change it to Sun.  That looks like the symptom I had after upgrading to Breezy.

If that's the case run:

sudo update-alternatives --config java

and pick the Sun JRE or JDK.

---

