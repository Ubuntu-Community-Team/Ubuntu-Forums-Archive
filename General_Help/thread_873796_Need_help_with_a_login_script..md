---
title: "Need help with a login script."
date: 2008-07-29
forum: General Help
---

### Post by Crix Maydine on 2008-07-29
Hi there,
I'm trying to get a script working that will start a timer once a user logs in and will countdown 1 hour. At 5 minutes and 1 minute I would like to be able to pop up a window with a warning that the session will be ending soon and any unsaved work will be lost. At the end of the timer I would like the computer to reboot.

I would really like to avoid any sort of kiosk software because it really doesn't suit my needs (for a library).  Unless there is a program that will run as a user without any server intervention that will accomplish this same task.

Thanks!

---

### Post by LowSky on 2008-07-29
Do you really want the computer to reboot, how about just log off?
I would say your better off writing three scripts, one for the 5 min warning, one for the one min warning (I'd make it a two min warning), then one to start shutdown.

this should help with timed shut down. just substitute for reboot or log off [http://dsl.org/cookbook/cookbook_41.html#SEC566](http://dsl.org/cookbook/cookbook_41.html#SEC566)

---

### Post by Green_Star on 2008-07-29
You can do it with a shell script. first edit sudoers so that you do not need to type password to use 'sudo reboot', write a shell script like below and put it in startup script so that it will start once you login into system.

sleep 3300
zenity --info session will be ending in 5min
sleep 240
zenity --info session will be ending in 1min
sleep 60
sudo reboot

---

### Post by Crix Maydine on 2008-07-29
Thanks!  Both those posts were extremely helpful.  I'll play around with what I've learned and hopefully I'll get it to work.

---

### Post by geirha on 2008-07-29
zenity --notification might be a nice option too. It's not well documented, so I'll show by example:

[php]#!/bin/bash

# This will start zenity, and it's stdin is linked to file descriptor 3
exec 3> >(zenity --notification --listen)

sleep 2
echo "icon:warning" >&3
echo "message:warning icon" >&3
sleep 2
echo "icon:info" >&3
echo "message:info icon" >&3
sleep 2
echo "icon:question" >&3
echo "message:question icon" >&3
sleep 2
echo "icon:error" >&3
echo "message:error icon" >&3
sleep 2
echo "icon:/usr/share/icons/Human/scalable/actions/back.svg" >&3
echo "message:go left!" >&3
sleep 2
echo "message:no, wait!" >&3
sleep 2
echo "icon:/usr/share/icons/Human/scalable/actions/forward.svg" >&3
echo "message:go right!" >&3
sleep 2

# close the file descriptor. This will also kill zenity.
exec 3>&-
[/php]

---

### Post by Crix Maydine on 2008-07-29
That is a really neat tool.  Once I get the technical stuff working that will be a great feature to take advantage of!  Thanks for that.

---

### Post by skotos on 2008-12-11
> **geirha said:**
> zenity --notification might be a nice option too. It's not well documented, so I'll show by example:

[php]#!/bin/bash

# This will start zenity, and it's stdin is linked to file descriptor 3
exec 3&> >(zenity --notification --listen)

sleep 2
echo "icon:warning" >&3
echo "message:warning icon" >&3
sleep 2
...
# close the file descriptor. This will also kill zenity.
exec 3>&-
[/php]

Very nice and valuable! I want to give my small contribution:[php]echo "tooltip:This is shown when hovering the applet" >&3[/php]

---

### Post by lvm on 2009-03-01
There is the fourth and the last command, "visible: false" hides notification icon, "visible: anything_else" shows it back again.

---

