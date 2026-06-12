---
title: "/etc/rc.local"
date: 2008-09-23
forum: General Help
---

### Post by ShareBuntu on 2008-09-23
Where would be the best place to execute a command like "touch /tmp/cold_boot"? I figured /etc/rc.local in my limited knowledge. I test for the existence of /tmp/cold_boot in .xsession - so I need the creation thereof to happen before .xsession is executed.

On a side note, I also have the following in /etc/rc.local:
```
echo -n 0x02 > /sys/module/hid/parameters/pb_fnmode #FN off (press fn for volume/brightness/etc)

echo 2500 > /sys/devices/platform/applesmc.768/fan1_min
```
The problem that I have is that when I resume from hibernation, these commands aren't executed. I'm on a MacBook and the former is used for pommed to control the inverted screen dim control I have going. The latter is to control the fan speed. Any idea how I can somehow execute those commands in a script executed at hibernation resumption?

Feedback on any one of the two issues would be greatly appreciated.

---

### Post by bingoUV on 2008-09-23
Does this help [http://ubuntuforums.org/showthread.php?t=875263](http://ubuntuforums.org/showthread.php?t=875263) ?

But I have a question. Going into hibernate won't delete the file /tmp/cold_boot. So why do you want to create the file on resume from hibernate? If it was created during boot, it will remain in existence through hibernation. Or do you want to change its last modification time by touch?

---

