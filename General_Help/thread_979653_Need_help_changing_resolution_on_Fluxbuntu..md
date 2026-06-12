---
title: "Need help changing resolution on Fluxbuntu."
date: 2008-11-12
forum: General Help
---

### Post by Junkbox on 2008-11-12
Ive tried "sudo leafpad /etc/X11/xorg.conf" to get root access to xorg.conf then edited the text to get my prefered resolution: 

SubSection “Display”
Depth 24
Modes “1024×768&#8243;
EndSubSection

The next time I reboot I get the splash screen but after it loads all I get is the command line. Any way to fix this? Ive looked at other threads on the forums about changing the resolution on fluxbuntu but no one mentioned this happening.

---

### Post by snowpine on 2008-11-12
Hi Junkbox, have you tried:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Junkbox on 2008-11-12
Worked perfectly! Thanks, Snowpine.

---

