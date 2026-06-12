---
title: "system freezes after login"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by estanton on 2009-11-08
I upgraded to Karmic yesterday on my Dell Inspiron 6000 after upgrading my desktop a couple of weeks ago. Everything went smoothly on the desktop but unfortunately something didn't work out on the laptop, now the system will freeze with a white screen after I log in, additionally the mouse does not work.
Does anyone know what the problem here could be? I'm prepared to just reinstall, what would be the best way to do that? Thanks.

---

### Post by dvlchd3 on 2009-11-08
Are you able to access any virtual terminal (Ctrl+Alt+F2) once you receive the white screen?  If so, post some logs:

```

tail /var/log/Xorg.0.log
tail /var/log/messages
tail /var/log/gdm/:0.log

```

If you can't access the virtual terminals, I'm thinking reinstall may be your best option...

---

### Post by estanton on 2009-11-08
yes I can access the virtual terminal. How can I get the logs from the virtual terminal onto a different computer or liveCD in order to post them on here?

---

