---
title: "Wicd will no longer boot! Whats going on!"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by havfunonline on 2008-01-23
I am trying to run a new network adapter.  I'm having a few issues with it, but I'm sure it'll get there.

It was showing up my network, I had the WEP key typed in, I clicked connect it got to "Obtaining IP address" did that for a while, then didn't connect.  So I tried typing in the IP address in manually, and it got to a loading stage and just kept going.  I pressed cancel, it kept going, I reloaded the program, it kept going, I rebooted my computer.... and Wicd wouldn't boot.

Now I can't connect to the internet, how can I force Wicd to load up, because I can hardly delete it and reinstall it, if I can't have the internet?

any ideas?

---

### Post by imdano on 2008-01-23
Try deleting the /opt/wicd/data/wireless-settings.conf file, then restarting the wicd daemon with ```
/etc/init.d/wicd start
```

---

