---
title: "Wicd drops WPA connection after a while"
date: 2009-04-20
forum: Hardware
---

### Post by deusdies on 2009-04-20
Hi there everyone,

I have Atheros AR5007EG chipset on my HP laptop. I'm sure you know how hard it is to get it working.

Well, finally I did it, by installing Wicd. Everything went perfectly well.

Now, I have two networks in range; one open, and the other one with WPA2 - PSK.

When I connect to the open one, everything works great. The speed is great, the connection is stable etc. However, when I connect to the WPA one, I get the connection (that is, I **am** able to go to the internet), but after a while (15-20 minutes), the connection drops. Even worse, I can't reconnect to either of the networks (it hangs on "Obtaining IP address" or "Validating Authentication", respectively).

Does anyone know how I can fix this?

Thanks!
-Bo

P.S. Maybe I should mention that the regular network manager **is** running in the background (although it doesn't connect; it "connects" to loopback only.)

---

### Post by deusdies on 2009-04-21
Please, anyone?

---

### Post by imdano on 2009-04-21
This sounds like a driver problem.  Once wicd makes a connection it is essentially hands-off.  It just checks to see that the connection is still there every few seconds.  The dropped connection is likely the work of a buggy driver, as is your trouble reconnecting afterward.  Does unloading/reloading your wireless driver allow you to get connected again?  You can do this with
```
sudo modprobe -r <driver name>
sudo modprobe <driver name>
```

---

