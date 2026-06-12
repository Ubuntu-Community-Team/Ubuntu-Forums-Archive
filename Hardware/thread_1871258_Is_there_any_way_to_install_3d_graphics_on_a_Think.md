---
title: "Is there any way to install 3d graphics on a Thinkpad r50e?"
date: 2011-10-28
forum: Hardware
---

### Post by Closrapexa on 2011-10-28
I have been using Ubuntu since 9.10, and like it, but recently moved to Xubuntu since the xfce desktop suited me more than unity. It works great, but is there any way to install 3d graphics drivers on my computer? If this has already been answered, as in, a really simple guide or step by step instructions, can anyone point me there? I know that my drivers were blacklisted or what have you, since they haven't really worked since 9.10, where they worked flawlessly, but is there a way to re-install them, or something?

Thanks :)

---

### Post by Toz on 2011-11-04
Which version xubuntu are you using? 

I believe this notebook has the intel driver. Are you currently using the intel driver? Posting back the contents of **/var/log/Xorg.0.log** would help identify which driver is in use.

As would the results of running the following commands in a terminal window:
```
lspci -vnn | grep -A 10 VGA
```
```
cat /proc/cmdline
```

---

### Post by Closrapexa on 2011-11-04
I managed to find a solution, forgot to update this thread. What I did was enable the disabled driver by creating the xorg.conf file (I had none) and pasting this in it. Now compiz works with all the effects: 

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Thanks anyway! I hope people find this thread and use it, since I had a hard time finding concise information anywhere

---

