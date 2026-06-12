---
title: "how to make a startup script?"
date: 2008-05-12
forum: Hardware
---

### Post by rmx on 2008-05-12
hi

I found a nice way to control cpu scalling on u8.04:
typing this on a terminal:

sudo modprobe cpufreq_userspace
sudo modprobe cpufreq_stats
sudo modprobe cpufreq_powersave
sudo modprobe cpufreq_ondemand
sudo modprobe cpufreq_conservative

however I have to type everytime my laptop restart.

how can I make a startup script to do this automatically?

thanks

RMX

---

### Post by otrojake on 2008-05-12
Just edit the /etc/modules file```
sudo gedit /etc/modules
``` and add each of those modules in there.  You don't need to include the "sudo modprobe" part, just the name of each of them.

---

### Post by DBrocks on 2008-05-12
You can do what he said. Or, you can do this, which will run ANY sript for you. 

1) first, create a script, and edit it to your needs. Lets say, you call it, autorun.sh
2) copy that script into /etc/init.d
3) run the following commands:
```
sudo update-rc.d autorun.sh defaults
sudo chmod +x /etc/init.d/autorun.sh
```

now it should run on startup.

~Dan

---

### Post by Ederico on 2011-09-25
Hello, is it possible to do a startup script and have Skype running once I login? If yes, how? Thanks beforehand.

---

### Post by .... on 2011-09-25
Skype doesn't need root permissions. Just add it to the startup programs in whatever desktop environment you're using. If you don't know how to do that, please tell us what desktop you're using (e.g. GNOME, Unity, KDE, etc.).

---

