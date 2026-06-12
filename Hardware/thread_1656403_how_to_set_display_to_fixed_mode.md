---
title: "how to set display to fixed mode?"
date: 2010-12-30
forum: Hardware
---

### Post by ottosykora on 2010-12-30
On on older laptop (dell C600) I need to reboot few times until I get display and all rest properly working. Mostly the screen flashes and remains then dark or I do not even see the login. 
The ubuntu definitely works and can find proper configuration, but how can I set this configuration so it will persist and the ubuntu will not tray next time again modprobe all display versions or all sorts of mouse etc.

I would like when it one time boots correctly, somehow fix the settings so next time they will be used and not searched for new settings.

How is this done?

---

### Post by pi/roman on 2010-12-30
You need to set up an X server configuration. There is a lot of information on it across the web but i will shamelessly point you toward my guide in case it may be of help.
[http://ubuntuforums.org/showthread.php?t=1401835](http://ubuntuforums.org/showthread.php?t=1401835)

Basically you create a file called xorg.conf file which will guide your computer through the boot-up process to be configured the way you desire. You will need to create modelines to place in your monitor section and reference them in the screen section. If you have a fancy geforce or ati video card, you may be able to find a utility to do all this for you but most old laptops don't have those.

---

