---
title: "Magic Mouse Scrolling"
date: 2010-01-02
forum: Hardware
---

### Post by zean on 2010-01-02
So I paired the Magic Mouse with Ubuntu using the Bluetooth Manager gotten from the Ubuntu repos, and by putting in "0000" as the passkey, it's worked wonderfully!

However, the darn thing seems to lack scrolling functionality. Has anyone had any luck trying to find such functionality?

---

### Post by davim on 2010-01-13
[http://github.com/cosmonaut/xf86-input-magicmouse](http://github.com/cosmonaut/xf86-input-magicmouse)

the problem is that the mouse doesn't send the touch feedback.
If only anyone could find a way to initialise the mouse so it thinks it is working with OS X and start sending the touch feedback.....

do you know of any tool similar to hcidump for OS X???

---

### Post by davim on 2010-01-25
It looks like this guy [http://github.com/entrope/linux-magicmouse](http://github.com/entrope/linux-magicmouse) is on the right path yo get the scrooling working on linux... :)

---

