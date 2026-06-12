---
title: "Keyboard issues"
date: 2010-07-02
forum: Hardware
---

### Post by RProgrammer on 2010-07-02
When I run normally everything works fine until a little after it gets to the log in screen: it does not respond to the mouse or keyboard, plays the drum beat 4 times, and drops off the network.

I can run in text mode, but if the console goes to sleep, the system crashes (apparently):  The display is blank (like normal sleep) but it won't wake when keys are pressed and it drops off the network (cutting active SSH connections, not listening on ports, doesn't ping)

When I run startx (from the user account), the screen mode changes but stays blank, the cursor appears, and the startup song plays but loops the last couple of seconds 4 times like a broken record.  The same system crashing happens (no input, no network).


I'm using Ubuntu 10.04 amd64.
uname -a: Linux casper 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux
Hardware is a Compaq Presario CQ61Z-400, ram: 1,837,576,192

---

