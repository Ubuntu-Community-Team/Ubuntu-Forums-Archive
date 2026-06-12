---
title: "Time display bug - reporting"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by patman0623 on 2009-11-01
Can someone let me know how to report a time display bug on the new graphical interface for Ubuntu? Please see attached image. I cannot even figure out what program it is to file the bug at launchpad.net

My time display is currently stuck at 4:01PM. 

[IMG]http://i49.photobucket.com/albums/f268/patman0623/badtime.png[/IMG]

---

### Post by patman0623 on 2009-11-01
Correction: not kubuntu, standard ubuntu 9.10.

---

### Post by Fr33d0m on 2009-11-01
Good question.  Id say Gnome Clock Applet, but I am not sure since time is set in System-Administration-Time and Date with time-admin.  I have the same issue and it doesn't matter if I use NTP or manual, or where I set the time.  The time is correct if I open a terminal and use date, if I go into time-admin, if I right-click on Gnome Clock Applet and choose Preferences or if I left click and view the time for my locale, all show the correct time.  Only the time displayed on the panel is wrong.

That said, my best bet is Gnome Clock Applet.  I'm still looking just in case someone else has solved it though.

---

### Post by Fr33d0m on 2009-11-02
Just realized you are using KDE--sorry.

Or not.  

If your time is stuck in the panel, but not elsewhere (open the terminal and type date) then go with the applet I mentioned above.  If you are using NTP then try a new server.

---

### Post by Fr33d0m on 2009-11-02
This might be a bug in NTP.  See [https://bugs.launchpad.net/ubuntu/+bug/459463](https://bugs.launchpad.net/ubuntu/+bug/459463)

Check out the screenshot he attached and note the commands he is using to trouble shoot.

---

### Post by patman0623 on 2009-11-02
No, not the same bug. Unfortunately, bug not replicating, so I can't re-report. :(

---

### Post by andrewabc on 2009-11-02
See if you can edit your first post and change kubuntu to ubuntu.

---

### Post by patman0623 on 2009-11-02
> **andrewabc said:**
> See if you can edit your first post and change kubuntu to ubuntu.No, unless I'm missing something.

---

### Post by andrewabc on 2009-11-02
> **patman0623 said:**
> No, unless I'm missing something.

Go advanced.

Really sucks if it can't be changed. :(
Darn forum software.

---

