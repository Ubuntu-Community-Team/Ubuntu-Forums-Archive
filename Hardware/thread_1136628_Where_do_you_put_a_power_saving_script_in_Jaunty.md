---
title: "Where do you put a power saving script in Jaunty ?"
date: 2009-04-25
forum: Hardware
---

### Post by Axx83 on 2009-04-25
Where do you put a power saving script in Jaunty ?

I need this script to be processed at start, when I unplug ac, when I plug it, when I suspend, when I get back from suspension and when I shut down/restart the notebook.

In Intrepid I putted it in:
/etc/pm/power.d
/etc/pm/sleep.d

but it wasn't run in all the cases I needed to, especially from suspend and restart.

Thanks for the help

---

### Post by cyprusxr3 on 2009-04-26
I'm having the same problems. Any help is appreciated.

UPDATE:

With some help from [this thread]("http://ubuntuforums.org/showpost.php?p=6902870&postcount=34"), I've found that the scripts can be put into subfolders in "/etc/acpi". It seems that every event has a scripts folder. I've decided I want my scripts to run on events "AC connect", "AC disconnect", "Startup", and "Resume". (This may be too many places or too few, but I haven't seen and problems yet).

So, the old
```
sudo install 99-savings /etc/pm/sleep.d
sudo install 99-savings /etc/pm/power.d
```
becomes
```

sudo install 99-savings.sh /etc/acpi/start.d/
sudo install 99-savings.sh /etc/acpi/resume.d/
sudo install 99-savings.sh /etc/acpi/ac.d/
sudo install 99-savings.sh /etc/acpi/battery.d/

```

This may or may not be the same functionality that sleep.d and power.d had in 8.10, but the script is now executing for me.

---

### Post by eldragon on 2009-04-26
in my arch linux install, when this happened, ive added a line running the script in 
/etc/acpi/actions/lm_ac_adapter.sh

---

