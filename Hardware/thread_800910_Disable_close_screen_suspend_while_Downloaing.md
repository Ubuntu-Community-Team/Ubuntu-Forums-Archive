---
title: "Disable close screen suspend while Downloaing"
date: 2008-05-20
forum: Hardware
---

### Post by nuclearpidgeon on 2008-05-20
Hi

I noticed recently when burning in Brasero that the suspend triggered b closing my laptop lid was temporarily disabled. I was wondering if I could rig this function so my laptop won't suspend if I'm downloading something (Mozilla Firefox).

Thanks in advance

---

### Post by eOgas on 2008-05-20
Well, the easiest way would be to simply change the settings in Power Management for the behavior when you close the lid.  This of course would have to be changed back if you wanted it to suspend when you aren't downloading.  You could perhaps write a script to do this automatically, but it seems like it would just be added work for something that you can do with a few mouse clicks.

I suppose you could write a script to change the setting depending on network traffic, but you would probably have to allow a small amount of traffic for various little things that download/upload small amounts of data.  I wouldn't know where to begin with a script like this, perhaps someone else knows how to write it.

---

### Post by sdennie on 2008-05-20
I don't know if there is an automatic way but, if you are downloading something large, you could try the inhibit applet.  Right click on a blank part of a panel and select Add to Panel.  Find the inhibit applet and click Add.  You should be able to turn off power savings features with that.

---

### Post by nuclearpidgeon on 2008-07-27
> **vor said:**
> I don't know if there is an automatic way but, if you are downloading something large, you could try the inhibit applet.  Right click on a blank part of a panel and select Add to Panel.  Find the inhibit applet and click Add.  You should be able to turn off power savings features with that.

Thanks, this works. But I still think there could be some way to automate this - eg a script that monitors LAN/WLAN and/or CPU activity, and if over a certain amount, automatically inhibit the sleep. I can see now that for laptop users, this would be really handy

Perhaps this could even hook into Firefox itself. Does anyone know if Firefox can use DBus to say that it is downloading something?

And perhaps Brasero uses DBus to say 'don't suspend'

---

