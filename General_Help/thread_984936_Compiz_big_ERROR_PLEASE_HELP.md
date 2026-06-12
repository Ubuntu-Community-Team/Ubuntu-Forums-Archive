---
title: "Compiz big ERROR PLEASE HELP"
date: 2008-11-17
forum: General Help
---

### Post by annamoo on 2008-11-17
Hello
My computer doesn't like something I did with the windows in compiz and now doesn't display any.  I can get to the command line from startup but can't even get to a terminal.
Any suggestions for resetting compiz from the command line?
Thanks,
annamoo :guitar:

---

### Post by eternalnewbee on 2008-11-17
Try **Ctrl-Alt-Backspace**, and login again.

---

### Post by annamoo on 2008-11-17
Thanks but it hasn't worked.

---

### Post by eternalnewbee on 2008-11-17
There's a window decorator plugin in CompizCconfigManager. Enabling it might solve your problem.
And if you can't do anything, you might have to reboot your system, and try again.
Hope this helps...

---

### Post by annamoo on 2008-11-17
I have restarted and stuff like that to no avail.

The problem is that I can't access the ubuntu GUI - the window management has gone. i.e. I can't enable a window decorator plugin or anything.

Think I need to reset compiz, or enable the plugin, from the command line but don't know how to do it.

---

### Post by eternalnewbee on 2008-11-17
```
metacity --replace
```
Does that help?

---

### Post by annamoo on 2008-11-17
I get an error message:
> Window manager error: Unable to open X display
Not worked!

---

### Post by annamoo on 2008-11-17
Here is the error message when i type 'compiz' into root:
> Checking for Xgl: xvinfo: Unable to open display not present
xset: unable to open display ""
xset q doesn't reveal the location of the log file.  Using fallback /var/log/Xorg.0.log
Detected PCI ID for VGA:
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity
Window manager error: Unable to clean open X display

---

### Post by annamoo on 2008-11-17
I did a system reinstall and it's okay now, was able to recover my files.

---

