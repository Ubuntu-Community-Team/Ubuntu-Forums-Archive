---
title: "How to disable Bluetooth on at autostart?"
date: 2010-10-17
forum: Hardware
---

### Post by rmx on 2010-10-17
Hi! 
I have a Ubuntu net remix.
It starts with Bluetooth turned on by default.
Is there a way to start with turned off instead?
Thank you

---

### Post by Quackers on 2010-10-17
System > Preferences > Startup Applications
The first entry in my screen is Bluetooth Manager. I unchecked that in mine. You can remove it as well if desired.

---

### Post by rmx on 2010-10-21
Thank you for your reply.
That way it disables the applet. So, I will not have it if I need to turn it on again.
I want to have the applet visible at notification area but with bluetooth turned off by default.
I guess I was not clear enough in my question. Sorry for that.
Cheers

---

### Post by Muster Mark on 2010-10-21
to turn bluetooth on when it is off: System > Preferences > Bluetooth

---

### Post by P4man on 2010-10-21
You guys are all missing the question; he wants the bluetooth radio turned off by default. Im surprised there doesnt seem to be an easy way to do this. 
But this should work:

First test it in a terminal:

```
sudo rfkill block bluetooth
```

If that turns off the radio, but lets you reenable it with the applet, then we are good to go

```
gksudo gedit gedit /etc/rc.local 
```

add this line:

```
rfkill block bluetooth
```

Thats it.

---

