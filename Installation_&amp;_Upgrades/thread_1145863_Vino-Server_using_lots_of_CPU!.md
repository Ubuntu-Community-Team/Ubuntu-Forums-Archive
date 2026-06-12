---
title: "Vino-Server using lots of CPU!"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by LonelyAppleHater on 2009-05-02
Just wondering if anyone has this problem.

The built-in vino-server uses way too much CPU resources as soon as it starts up. If you do a top, you'll see the Xorg process hogging the CPU, but turning off vino-server in the Preferences -> Remote Desktop gets everything back to normal.  

I did find a solution, and that's to use x11vnc.  It uses WAY less resources than vino-server, and I get way less freezes and disconnects when connecting to it from a client.  

Instructions on how to set it up here:

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

I changed the last line and used Jaunty's new notification feature to tell me when VNC is started and the port:

```

notify-send "VNC Started" "Your VNC port is `cat ~/.vnc/port.txt`"

```

Hope this helps someone, as I was tearing my hair out trying to figure out what was making the CPU's so busy after a reboot.

Good Luck!

---

