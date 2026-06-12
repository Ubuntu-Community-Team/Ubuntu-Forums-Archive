---
title: "Gnome messed up after installing AWN dock"
date: 2008-09-05
forum: General Help
---

### Post by Telémakhos on 2008-09-05
Hi all,

I was installing AWN following this tutorial:

[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

As it says, I've deleted the gnome-panel from the startup and after finishing step 2, I've rebooted and nothing appears in my sudo user desktop. Only the wallpaper and the cursor (without right click menu). Pressed ALT+F2 and terminal does not appears... Dunno what I've done wrong.

I can boot correctly with the gnome safe mode. What can I do to return to the previous gnome settings of my sudo user? :(

Edit: Ok.. I think that I know what I've done. When finishing tip 2 of that howto...

> First, delete the alternative (bottom) GNOME panel, if you have one. Now comes the tricky part, because the remaining panel can't be deleted. So, go to System -> Preferences -> Sessions and click the second tab, "Current Session". Click once on the gnome-panel entry in that list and then hit the 'Remove' button to delete the last remaining panel. Then, click on the "Session Options" tab and check the 'Automatically remember running applications when logging out' option and hit the 'Remember currently running applications' button. Close the Sessions window and reboot the computer.

I pressed the 'Remember currently running applications' button when the system was going down... OMG... Is this possible? Now I start and I only find the cursor and the wallpaper.. What can I do to reset this settings? Should I load one by one with a  terminal?

---

### Post by fooman on 2008-09-05
if alt-f2 does not get you a "run application" box and you cannot get to a terminal....then this is what i would do

press ctrl-alt-f1 

that will drop you to another session, *but with no gui*...when you get to that screen, log in with your user name and password.  then type this command:

```
sudo apt-get install nautilus-open-terminal
```

press enter.  after it finishes installing, reboot.  when you get back to your desktop,  right click on any part of the screen and choose "open in terminal"

when the terminal window opens, type this command:

```
gnome-panel &
```

press enter and you should get your top panel back.  right click in the top panel and choose "add panel" to get the bottom panel back.

---

### Post by Telémakhos on 2008-09-05
> **Telémakhos said:**
> 
As it says, I've deleted the gnome-panel from the startup and after finishing step 2, I've rebooted and nothing appears in my sudo user desktop. Only the wallpaper and the cursor **(without right click menu)**. Pressed ALT+F2 and terminal does not appears...


:(

---

### Post by yjwong on 2008-09-05
Heh. Here's where the console comes into use again (:

Once you log into GNOME (blank desktop and curson only), switch to console mode by pressing Ctrl + Alt + F1, then use the following command to start a Terminal:

```
DISPLAY=:0 gnome-terminal
```

Switch back to GNOME by pressing Ctrl + Alt + F7, type in "gnome-panel" (as instructed by the previous member), and you should see the Panel loading. From there on you can continue troubleshooting.

---

### Post by Telémakhos on 2008-09-05
Hi yjwong, tried it and I get a blank box in the left/up corner. However I cant type in... It's like a terminal that doesn't load correctly

Is there any way to manage the startup processes of the user sessions only with a terminal? I bet it's possible... I would need to know what file stores this values in order to edit it with nano or any editor...

Or what can I do?

---

### Post by Telémakhos on 2008-09-05
Well, time to study...

[http://linux.about.com/library/cmd/blcmdl1_gnome-session.htm](http://linux.about.com/library/cmd/blcmdl1_gnome-session.htm)

wish me luck...

---

