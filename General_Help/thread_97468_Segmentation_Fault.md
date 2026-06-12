---
title: "Segmentation Fault"
date: 2005-12-01
forum: General Help
---

### Post by cclemon on 2005-12-01
Hi. I'm getting loads of errors with the errormessage "segmentation fault".

I didn't know what happened because the applications (like Firefox, Evolution , gnome-??? apps) just closed it self without any warnings. So i tried to run them from the console, and get the "segmentation fault" message on many of the apps that crashes.

Example from the console:

Firefox:
```
ends with the message "segmentation fault"
```

Evolution: 
```
adding hook target 'source'
(evolution:8788): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed
```

/usr/bin/gnome-sudo (that runs every time I try to run root privilege apps like Synaptic):
```
line 3:  8894 Segmentation fault       /usr/bin/gksudo "$@"
```

and so on.

I just cant find out what I've done wrong since I haven't installed or edited anything to get the errors...

---

