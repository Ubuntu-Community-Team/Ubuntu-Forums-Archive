---
title: "Fan Control (Asus Eee 1005HA)"
date: 2009-09-12
forum: Hardware
---

### Post by rowan_m on 2009-09-12
My Asus Eee 1005HA seems like it's running a little hot and the fan doesn't seem to kick in. Does anyone know if there's a way to configure when the fan kicks in, or some kind of manual way to trigger it? The sensors definitely pick it up properly when it runs, but I'd prefer not to wait until about 75 degrees for that to happen.

Any pointers to scripts or configuration much appreciated, Eee-specific or just fan control in general.

---

### Post by rowan_m on 2009-09-13
Think I found what I was after in:
```
/etc/default/eeepc-acpi
```Specifically:
```

# Set this to "managed", "auto", or "disabled".  When set to "managed" the utilities provided in this package will manage
# your fan for you and you will be able to set thresholds by altering the TEMP values below.  When set to
# "auto" the fan will be managed by your BIOS.
# Set to "disabled" to stop the fan process from executing, leaving the fan shut off (NOTE: A 'sudo eeepc-restore
# start' is required to turn the fan back on after disabling)
FAN_MODE="managed"

# Eee PC temperature control settings (only applies if fan is managed). These values are in Celcius, and when
# the temperature rises above the defined value, the fan management utility will increase fan speed until the
# temperature is reduced back below the threshold.

TEMP_NORMAL=55
TEMP_WARN=60
TEMP_CRIT=65

```

---

### Post by T3CHKOMMIE on 2009-09-21
hi guys. im still having problems with my fan. and my batterie for that matter. 

when i charge my battery and use my 1005ha-p at the same time. it over heats and locks up. i have to charge it when the pc is shutdown. :( not fun.  i can run my net book to about 60 celsius, fan NEVER changes speed. i have messed with the eee pc file and set it to manual and also to auto for the bios to control it. 

never the less my system continues to over heat and its really frustrating having to always run it off the batt, or shut id down to let it cool... 

any ideas? ive tried fancontrol but cant get it to respond at all... im really hoping this gets fixed in 9.10... if not.. im afraid i might have to reconsider os...*gulp*.

---

### Post by rowan_m on 2009-09-22
Yeah, "managed" doesn't seem to do much for me; the fan always stays off. I've set it to "auto" now and it comes on. However, it just seems to stay on all the time.

---

### Post by T3CHKOMMIE on 2009-10-03
i think i figured out my problem, i think i had two apps controlling the fan at the same time. after i uninstalled a version of eeepc-tray, and i set the config file to FAN="auto" the fan seemed to do its job, even though it still gets ridiculously hot when im plugged into the wall adapter. i DO hear the fan automatically change speeds when it gets under load.

---

### Post by onesojourner on 2009-12-02
I have eee controll installed. I don't think my fan is coming on properly either.

---

### Post by warmnscsi on 2010-05-09
I have the same problem with my 1005ha but I don't have 
/etc/default/eeepc-acpi

---

### Post by MarkieB on 2010-12-10
no longer participating in ubuntuforums.org

---

