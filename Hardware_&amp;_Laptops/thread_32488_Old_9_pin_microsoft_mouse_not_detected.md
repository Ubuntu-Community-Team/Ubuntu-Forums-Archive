---
title: "Old 9 pin microsoft mouse not detected"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by dustfinger on 2005-05-07
Ubuntu did not detect my old serial port mouse.  I think it is a serrial port.  It is one of those 9 pin ports and that is a serrial port correct?  Anyway, Ubuntu does not detect it.  So I grabbed my usb mouse from my laptop and plugged that in.  I then edited the xorg.conf file and changed /dev/input/mice to /dev/ttyS0 hoping that Ubuntu would detect the mouse on reboot.  Well now neither mouse is detected and when I press Ctrl-Alt-BkSp to drop out of X the system just ends up rebooting.  How can I solve this problem?  If I could simply edit the xorg.conf file again I could at least get my usb mouse working and that would allow me to expleriment until I can figure out how to get the older mouse working.  Any suggestions.  Thanks.

dustfinger.

---

### Post by dustfinger on 2005-05-08
I was able to gain terminal access by pressing Alt-F1 and that allowed me to use the keyboard to select a terminal from the menu options.  I am still unable to get the old mouse working though.  So far I have tried:

Option "Device" "/dev/ttyS0" 
and 
Option "Device" "/dev/ttyS1" 
neither of which work.  I am using :
Option "Protocol" "ImPS/2"

dustfinger.

---

### Post by dustfinger on 2005-05-08
Okay I solved the problem.  I had to set the protocol to "Microsoft"  Augh.  So.

Option "Device" "/dev/ttyS0" 
Option "Protocol" "Microsoft"

Worked for me.

dustfinger.

---

