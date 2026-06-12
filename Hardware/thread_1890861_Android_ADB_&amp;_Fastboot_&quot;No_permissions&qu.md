---
title: "Android ADB &amp; Fastboot &quot;No permissions&quot;"
date: 2011-12-04
forum: Hardware
---

### Post by merkourio on 2011-12-04
Hey guys,

I was trying to set up ADB and Fastboot for my Android phone on Ubuntu for some weeks now, without any success.. I have now installed everything according to the guide at [http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62]("http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62"), but everytime I search for devices i get this:

```
List of devices attached 
????????????	no permissions

```

I have tried everything stated in the guide, with no luck for the time being. It is really frustrating, as this issue might be the one to lead me to install back Windows as a secondary OS.

Do you have any tips? Thaks alot!

---

### Post by dave0109 on 2011-12-05
I've had this before, as I recall, I restarted the server with root permissions. So:
```

adb kill-server
sudo adb start-server

```

---

### Post by rojovilla on 2012-02-11
> **dave0109 said:**
> I've had this before, as I recall, I restarted the server with root permissions. So:
```

adb kill-server
sudo adb start-server

```

This is what worked for me.  Searched and read everywhere, but for some reason, this is the only that allowed adb to be restarted.  All the other tutorials don't even mention using sudo for the restart (duh!). Thanks, dave0109!

---

### Post by elgatofelix79 on 2012-07-06
What I did was just run:
     >sudo ./adb [command]
or in fastboot mode I ran:
     >sudo ./fastboot [command]
I had no need to kill-server and restart = )

---

### Post by scue on 2013-06-08
sudo chown 0:1000 $(which adb) 
sudo chown 0:1000 $(which fastboot)
sudo chmod u+s $(which adb)
sudo chmod u+s $(which fastboot)
sudo chmod 755 $(which adb)
sudo chmod 755 $(which fastboot)

---

### Post by oldfred on 2013-06-08
Thread Closed - old

---

