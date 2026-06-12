---
title: "no startx with breezy's xorg?"
date: 2005-11-16
forum: General Help
---

### Post by chipmonk010 on 2005-11-16
so im using ubuntu for my mythtv box...i was running hoary with some breezy packages just fine, then i installed transcode. this depended on the breezy version of xorg and it is causing me all kinds of problems. 
problems:
i want to start x from the command line, no gdm
i want to start mythfrontend automatically when x starts
theres no startx script and no .xsessions file which is what i used to use to accomplish this
what do i have to edit to make this happen?
also i get this error when i try to run $X as any user but root:
cannot move old log file ("/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old")
can i just change the permissions on this file or what should i do?

please any help would be great

---

### Post by oskude on 2005-11-16
never done that, but this site could be helpfull
[http://www.abarbaccia.com/](http://www.abarbaccia.com/)

---

### Post by chipmonk010 on 2005-11-16
thanks oskude but I figured it out i will now answer my own questions for the greater good lol....

the no startx problem was solved by running:
#apt-get -u dist-upgrade

being half hoary half breezy made x install weird i guess, after this i have my good ol friend startx back

as for this error: cannot move old log file ("/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old")
the solution was simply:
#chmod u+s /usr/X11R6/bin/Xorg

and im back in business
im now recompiling and installing ivtv for the breezy kernel (2.6.12)
anywho sry to take up space with this thread, perhaps when im done ill put a guide together for mythtv(there may already be one on this forum, i havent looked)

thanks anyway tho

---

