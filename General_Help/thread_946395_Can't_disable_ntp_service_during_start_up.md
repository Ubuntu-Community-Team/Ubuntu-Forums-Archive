---
title: "Can't disable ntp service during start up"
date: 2008-10-13
forum: General Help
---

### Post by johnny42 on 2008-10-13
I'm trying to disable the ntp service from starting up at boot time,
I used the command **update-rc -f ntp remove** to remove the system startup links but the service still starts at boot time,
I don't understand!
Any help would be great

---

### Post by justleen on 2008-10-13
is it called ntp, or ntpd?
Are there any script left in the rc.d directory?
```
 find /etc/init.d/ -name "*ntp*" 
```

---

### Post by johnny42 on 2008-10-14
Thanks justleen,
Its the ntp script which starts the ntpd program.
I checked the rc.d directories and there are no scripts for ntp but it still starts at boot time, very weird!

---

