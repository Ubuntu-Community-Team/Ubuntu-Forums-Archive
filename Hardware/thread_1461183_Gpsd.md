---
title: "Gpsd"
date: 2010-04-23
forum: Hardware
---

### Post by gandhioftherillo on 2010-04-23
How do I prevent gpsd from running automatically? Even after I run 
```
sudo /etc/init.d/gpsd stop
```
I still get: 
```
gpsd: Maybe gpsd is already running!
```

Thanks in advance!

---

### Post by gandhioftherillo on 2010-04-24
UPDATE: 
I ran 
```
sudo dpkg-reconfigure gpsd
```
to shut off the auto-running of gpsd (it modifies the /etc/default/gpsd file) and did a reboot.
Gpsd is still starting on it's own and I keep getting
```
gpsd: Maybe gpsd is already running!
```

I've been doing some Googling, but haven't found anything terribly useful

---

### Post by tgalati4 on 2010-04-24
Check your configuration files in /etc/default--which you did presumably.  Several programs (like gpsdrive) start gpsd (if not already started), so if you have anything else running or started at boot, gpsd will get started as well.

Try:

sudo killall gpsd

---

