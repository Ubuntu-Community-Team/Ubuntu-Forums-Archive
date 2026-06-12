---
title: "Laptop system beep"
date: 2008-05-12
forum: Hardware
---

### Post by pamplepoo on 2008-05-12
Hello

I'm new to linux, I've had Hardy Heron (yes? The latest kubuntu? why so many names for one system?!) on my laptop for about a week. My brother was really helpful in showing me some of the ropes, but I still don't know what half of this stuff is!

ANYWAY, I have a problem, and that is that I work in a library, and I can't figure out how to mute/get rid of a system beep (main example is when I hit backspace one too many times in pidgin)

I've tried google, and all i've been getting have been for older releases, and I'm not savvy enough to work around the changes :/

Thank you!

---

### Post by brew1brew on 2008-05-12
click on your K menu then "system settings".
Then click on "Notifications" under & feel section.

you now can adjust all your notifications from there.

Hope this helps
Les

---

### Post by pamplepoo on 2008-05-12
I turned off all sounds, and I have it on mute, but that sound still happens- its something not connected to the main speakers :/

---

### Post by Ayuthia on 2008-05-12
You could try the following:
```
sudo modprobe -r pcspkr
```
If that fixes the problem, you can add it to the blacklist:
```
echo blacklist pcspkr|sudo tee -a /etc/modprobe.d/blacklist
```

This is the module that makes the system beep.  It is different than your sound card.

---

### Post by pamplepoo on 2008-05-12
Thank you, it worked!

---

