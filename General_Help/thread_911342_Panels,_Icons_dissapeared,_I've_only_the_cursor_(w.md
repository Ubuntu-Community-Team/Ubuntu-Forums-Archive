---
title: "Panels, Icons dissapeared, I've only the cursor (without right menú)"
date: 2008-09-05
forum: General Help
---

### Post by Telémakhos on 2008-09-05
Hi folks, 

I was installing the AWM dock following a howto and I deleted the botton gnome panel. But I've made some mistake...

I've gone to System>Preferences>Session and I deleted gnome-panel... after this and still following the tutorial I configured the user session to start with this preferences 

I've done this following the tutorial... and now I log in as my sudo user and neither the superior panel nor the bottom appears! The mouse right click menu doesnt works and I can't open a terminal pressing ALT+F2. And compiz doesnt run...

WTH I've made? What can I do? :confused:

---

### Post by davidpeace on 2008-09-05
This may not help, but recently an announcement was made about some malicious users posting bad commands/advice that had new users mistakenly messing up their system. Get the attention of a moderator and point them to the HOWTO you used. In the meantime, reboot the entire system and when the prompt comes up, at the very beginning for alternate startup options (on some machines you hit esc or on some f11...) select the recovery mode and see if you can undo whatever you did to make the panels disappear that way. Good luck.

---

### Post by Telémakhos on 2008-09-05
Hi David,  I think that I know what I've done. I was installing AWN following this tutorial:

[http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

When finishing tip 2 of that howto...

> First, delete the alternative (bottom) GNOME panel, if you have one. Now comes the tricky part, because the remaining panel can't be deleted. So, go to System -> Preferences -> Sessions and click the second tab, "Current Session". Click once on the gnome-panel entry in that list and then hit the 'Remove' button to delete the last remaining panel. Then, click on the "Session Options" tab and check the 'Automatically remember running applications when logging out' option and hit the 'Remember currently running applications' button. Close the Sessions window and reboot the computer.

...I pressed the 'Remember currently running applications' button when the system was going down... OMG... Is this possible? Now I start and I only find the cursor and the wallpaper.. What can I do to reset this settings? Should I load one by one with a  terminal?

Edit: Forgot to mention: I cant open any terminal! ALT+F2 doesn't work! :_(

---

### Post by davidpeace on 2008-09-05
You should be able to get a terminal by rebooting the entire system (log out, shut down, turn power off, turn back on...) Follow previous post and try the recovery mode. Check out this thread:

[http://ubuntuforums.org/showthread.php?t=902763&highlight=lost+panels+launcher](http://ubuntuforums.org/showthread.php?t=902763&highlight=lost+panels+launcher)

---

