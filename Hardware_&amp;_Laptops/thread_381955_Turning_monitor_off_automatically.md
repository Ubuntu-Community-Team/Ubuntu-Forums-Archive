---
title: "Turning monitor off automatically"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by Coldmiser487 on 2007-03-11
I found this webpage [http://gentoo-wiki.com/HOWTO_Automatically_turn_off_your_monitor]("http://gentoo-wiki.com/HOWTO_Automatically_turn_off_your_monitor")    that shows how to turn your monitor off automatically using Gentoo.  I tried to follow the instructions on Ubuntu, but so far, no luck.
Does a solution exist for ubuntu or can someone get this working.  
It's quite possible I'm doing something wrong because I'm not too familiar with linux. 

Thanks

---

### Post by kerry_s on 2007-03-11
Have you tried setting it up in power management?
You can try using xset, put this command in your auto start and it will set you screen to turn off in about 5min of inactivity.

xset dpms 0 0 300 

in terminal:
xset -q

to see your settings.

You can also create a launcher to click on to turn the screen off, the command->

sleep 5 && xset dpms force off 

This gives you 5 seconds to take your hand off the mouse.

---

### Post by Coldmiser487 on 2007-03-11
Thanks for your help Kerry
I did try to change it in power management, but it didn't turn off the monitor.
The command xset dpms 0 0 300 did solve the problem, 

Only other question I have is where or HOW (more specifically) do I put it in auto start?
I appreciate all your help.

---

### Post by kerry_s on 2007-03-12
Look under administration> session> autostart,it is the last tab

I don't use gnome so you might have to look around.

---

### Post by Coldmiser487 on 2007-03-12
thanks again

---

### Post by Coldmiser487 on 2007-03-12
Would this also work if I put a script in the /etc/rc0.d directory?
That way it would take effect even if I never logged into the GUI?

---

### Post by kerry_s on 2007-03-12
You can put it in /etc/rc.local ,but just to let you know that some window managers will overwrite the settings at login, can't remember if gnome does that. You still have to have it at start up on the user level.

All settings run here as root:

sudo gedit /etc/rc.local

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

xset dpms 0 0 300 &

exit 0

```

After you log in you can check if the setting is set, in terminal> xset -q

---

### Post by Coldmiser487 on 2007-03-12
Cool.  I put it in both places that way I think I'm covered.

Thanks again.

---

