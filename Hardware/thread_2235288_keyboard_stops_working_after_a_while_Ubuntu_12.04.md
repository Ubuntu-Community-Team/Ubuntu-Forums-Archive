---
title: "keyboard stops working after a while Ubuntu 12.04"
date: 2014-07-20
forum: Hardware
---

### Post by pegasusgr on 2014-07-20
It has happened a few times that my laptop's keyboard stops working after several hours on a session. Has anybody else faced this problem? What can I do?

---

### Post by tgalati4 on 2014-07-20
Open a terminal:

```
dmesg | tail -50
cat /var/log/Xorg.0.log
```

Of course if your keyboard is frozen you can't type those commands, so look for a USB keyboard and keep it handy.  Plug it in and see if you can continue to type.  If not, then perhaps your machine is frozen and not just the keyboard.

Your machine might need cleaning.  When the machine is off, turn it over with the keyboard against a table.  Bang on it like bongo drums.  Lift up the laptop.  Be simultaneously amazed and grossed out.

It could be a heat-related issue.  Perhaps the ribbon cable under the keyboard is loose and needs reseating.

---

### Post by pegasusgr on 2014-07-20
Thanks, I'll try that if it ever happens again.

I'm sure that the machine is not frozen as my USB mouse works fine and I can use the on-screen keyboard to type commands.

---

### Post by pegasusgr on 2014-07-28
Hi again,

It just did it again right now! It's funny because as soon as I plugged in the usb keyboard as you suggested, my laptop's keyboard started functioning again!

Please see attachment for the output of the commands you suggested. Do you know whether I can do anything? Thanks a lot.

---

