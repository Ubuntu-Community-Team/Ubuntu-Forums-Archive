---
title: "INTEL ALC883 soundcard no sound/low volume"
date: 2009-01-24
forum: Hardware
---

### Post by kakyoism on 2009-01-24
My INTEL ALC883 soundcard has a very low volume even tuned to max.
So I referred to this post:
[http://ww.ubuntuforums.org/showthread.php?p=6416435](http://ww.ubuntuforums.org/showthread.php?p=6416435)

and add a line 
```
options snd-hda-intel model=MODEL_NAME 
```
to the end of 
```
/etc/modprobe.d/alsa-base 
```

But no matter which module name I tried from that list of modules, I lost the sound entirely after a reboot.

Help!

---

### Post by kakyoism on 2009-01-24
Update:

After I reboot, I saw an error dialog:

With the title:
```
An error occurred while loading or saving configuration information for gnome-volume-control. Some of your configuration settings may not work properly.
```

and detail:
```

Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
Adding client to server's list failed, CORBA error: IDL:omg.org/CORBA/COMM_FAILURE:1.0
```

---

