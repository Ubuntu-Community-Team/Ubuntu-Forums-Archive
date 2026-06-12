---
title: "Turning off computer."
date: 2008-11-25
forum: General Help
---

### Post by kendzi on 2008-11-25
Hi. 

I try to turn off computer but it don't work. After I click power off button I get message in logs :

WARNING: Unable to stop system: Not privileged for action: org.freedesktop.consolekit.system.stop no

I use ubuntu 8.10 and gnome is run using vnc4server.

---

### Post by lukjad on 2008-11-25
Umm... when you say press the button, do you mean the button on the case or the button in *System->Shut Down*?

---

### Post by kendzi on 2008-11-25
I click at menu System->Shut Down > Shut Down, but nothing happen only message in logs.

---

### Post by oaxacamatt1 on 2008-11-25
Hi Kendzi,
Try this...
goto your command line and enter:
gksu gedit /etc/init.d/alsa-utils
goto the first 'stop)' in the file and insert the following commands:
ifconfig eth0 down
ifconfig wlan0 down
then save the file and try it again.  Appearently the problem is due to the ethernet card or wifi cards are not shut down so it hangs the system.  It happened to me too.

I AM NOT Guaranteeing this will solve the problem but this is what I found on the fourms too.

Hope this helps,
Matt

---

### Post by kanikilu on 2008-11-25
> **kendzi said:**
> Hi. 

I try to turn off computer but it don't work. After I click power off button I get message in logs :

WARNING: Unable to stop system: Not privileged for action: org.freedesktop.consolekit.system.stop no

I use ubuntu 8.10 and gnome is run using vnc4server.

I haven't played around with these settings much, but might be worth looking into...

Try running "polkit-gnome-authorization" on the computer you are connecting to via VNC (the computer that won't shutdown when you are connected to it remotely) and then browse to:

org -> freedesktop -> consolekit -> system

Click on "Stop the system", then click "Grant", then use the dropdown to select your user account, select "None" under constraints and click "Grant".

Of course...if you can get to a terminal on the remote computer, you could always just use "sudo shutdown -h now". PITA, though if you have to do it like that everytime...

---

### Post by kendzi on 2008-11-25
It work !

I try before use System > Authorization ("polkit-gnome-authorization") but "Grant" button was always disabled :(

Help running this with command:
gksu polkit-gnome-authorization

So thanks !

---

