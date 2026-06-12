---
title: "New Install Boot Problem"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by Rubicon421 on 2009-10-25
I just installed 9.04 32 bit. I used the option that lets the installer use the whole HD and choose the partitions automatically. It installed fine and restarted. Then I ran the update wizard and installed all updates and also activated the recommended third party driver for my video card. That is the only change I had made from a fresh install. On the next reboot it goes to the command prompt and asks for a login name. I am able to log in but then it just goes to the new prompt that shows I'm logged in and won't go to the desktop. 

It says-
 'user name'@'computer name':~$
what do I do from there to get back to the GUI and how do it make it restart to the GUI automatically next time? Why is it doing this in the first place?

---

### Post by ajgreeny on 2009-10-25
Having logged in to the command line, try typing ```
startx
``` to see if you get to the gui.  If you do, you then could try the command ```
sudo /etc/init.d/gdm restart
```
Now try a reboot, or maybe just logout and in again, to see if you get to a gui automatically.

---

### Post by Rubicon421 on 2009-10-25
tried both, with the following results. 

startx-

Fatal server error:
no screens found

xinit: no such file or directory (errno 2) unable to connect to x server.......


sudo etc/init.....

stopping GNOME dixplay Manger...  [OK]
stopping GNOME dixplay Manger...  [OK]

back to prompt

Not sure what's going on, I didn't change anything other than the updates and driver I mentioned.  Safe mode does the same thing.

---

### Post by Mark Phelps on 2009-10-25
You don't have an ATI card by any chance, do you?

If so, you can try removing the ATI drivers from the command line using the link below and at least, with the open source drivers, you will have a working desktop:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Rubicon421 on 2009-10-25
still no luck. I'm just going to reinstall it and not use the third party driver this time. There were two that it listed and I chose the recommended one. Do you think I should try the other one this time or just stick with the generic one? I would like to be able to use Compiz so I think I have to find a working third party driver right?

---

