---
title: "xorg.config has no input section from which to enable shm"
date: 2010-04-18
forum: Hardware
---

### Post by artshark on 2010-04-18
hey guys! i am looking to enable shmconfig to see if i can get multitouch gestures. in trying to add the input sections of this file, the graphical layer is messed up. i've fixed that, but still am unaware how to enable shmconfig. any pointers?
thanks!
Art

---

### Post by pi/roman on 2010-04-18
Open your hal configuration and include or uncomment this line:

<merge key="input.x11_options.SHMConfig" type="string">true</merge>

---

### Post by artshark on 2010-04-18
> **pi/roman said:**
> Open your hal configuration and include or uncomment this line:

<merge key="input.x11_options.SHMConfig" type="string">true</merge>
how do i do that?
thanks!

---

### Post by pi/roman on 2010-04-18
This will list your hal configuration files:
sudo find /usr/share/hal /etc/hal -name *synaptics.fdi -print0 |  xargs -0 -t cat

Then you can use gedit to enter the appropriate lines
gksudo gedit [COLOR=DarkOrchid]"path to configuration file"[/COLOR]
Where [COLOR=DarkOrchid]"path to configuration file"[/COLOR] will be listed in the first line from the previous command.

---

