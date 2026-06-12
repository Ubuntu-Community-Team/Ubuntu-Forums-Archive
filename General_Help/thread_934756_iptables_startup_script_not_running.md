---
title: "iptables startup script not running"
date: 2008-09-30
forum: General Help
---

### Post by Shwick2 on 2008-09-30
I'm running ubuntu 8.04 and my iptables startup script isn't running during startup.  I know this because when I start my linux machine, login and do a "sudo iptables -L" I see the three default accept strategies.  I have to quickly run the script after I login to enable my rules.

 I copied the file "iptablesStartup" into /etc/init.d/ and did a "chmod 755" to make the permissions match the other scripts.  I made sure the first line of the script was #!/bin/sh.  I restarted a few times, still didn't work.

 I disabled ufw, but could iptables be getting overwritten somewhere else?  I just can't see anything wrong with the script.

---

### Post by Locutus_of_Borg on 2008-10-01
set your rules then exectue iptables-save >> /etc/iptables.rules
followed by
rc-update add iptables default
and/or
add the path to the executable into /etc/conf.d/local.start

assuming ubuntu has these utilities

also make sure the init script points to /etc/iptables.rules as the location for your rules

---

### Post by webaake on 2008-10-01
If the above doesn't work, rc.local is also a good place. rc.local executes as root during startup.

More info in the file /etc/rc.local itself.

---

### Post by Shwick2 on 2008-10-01
In ADDITION to adding your script to /etc/init.d, you have to execute the following command: sudo update-rc.d iptables defaults.  Everywhere I see people saying just add the script to /etc/init.d, but I never heard anything about update-rc.d.

---

