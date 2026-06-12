---
title: "Authorize a script with Visudo"
date: 2008-11-17
forum: General Help
---

### Post by jbrown96 on 2008-11-17
Someone has graciously given me a script to fix the video display on my TV; however, I don't know how to get it to run automatically. There are two scripts: one is in my ~/.kde/Autostart folder and obviously needs to be autostarted and the other is in /usr/bin and is referenced by the other script. Both of them need to run as root and they use a utility (aticonfig) that also needs to be root. The user said that I need to "add" them to my visudo file to get them to work properly. Does anyone know how I can get these to run as root? Do I need to add all three? 

I've looked at the file and understand basically what it does, but I can't figure out how to add specific scripts to it.

Thanks for the help

---

### Post by Marcus Derekus on 2008-11-17
Open up terminal and type:

```
sudo gedit /ect/rc.local
```

Now add the line in red. (replace FILE'S NAME with the file in Autostart only) :

Then save

```


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="Red"]sudo /home/YOUR HOME DIR'S NAME/.kde/Autostart/FILE'S NAME[/COLOR]

exit 0
```

Please post results

---

