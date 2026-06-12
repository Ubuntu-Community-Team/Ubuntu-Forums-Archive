---
title: "Help - changing from Ubuntu to Kubuntu"
date: 2008-11-11
forum: General Help
---

### Post by ozguitarplayer on 2008-11-11
Hi everyone,
I'm new to Ubuntu...
Installed Ubuntu and all works well however I wanted to try Kubuntu desktop and downloaded the files...all good...then I got on the screen

nigel@nigel-desktop:~$ 

with the cursor flashing and waiting for me...and I don't know what I'm to fill in.
Is there a set response that I'm to fill in at this point?

---

### Post by dcast on 2008-11-11
Do you mean you opened up a terminal window? If so you don't need to do anything, its only a matter of if you want to. If your GUI (graphical user interface) isn't working then you might want to try typing 'startx'. How did you install Kubuntu using 'sudo apt-get install kubuntu-desktop' because that will install Kubuntu for you if you already have Ubuntu working. Need some more details on exactly what the problem is.

---

### Post by Mr_JMM on 2008-11-11
Personally I wouldn't do this (add KDE to Ubuntu). If you have the room, create a separate partition for Kubuntu and dual boot.

This is what I did as when I wanted to convert back to Gnome (Ubuntu) i couldn't get everything looking right again and not everything worked 100% as well as it should have done (Kopete being one example).
This way it's so much easier to go back to whichever version you prefer and / or you can fully test both side by side.

---

### Post by ozguitarplayer on 2008-11-11
thanks for the replies...
I didn't open anything except start up Kubuntu and then I get the screen with that in it and I can't exit the screen and cannot proceed until I've responded to the waiting cursor...

---

### Post by dcast on 2008-11-11
In that case, type 'startx' then hit return. Post what happens here.

---

### Post by jrharvey on 2008-11-11
```
startx
```

---

### Post by ozguitarplayer on 2008-11-11
If I type in; 
startx 
the reply is;
x:user not authorized to run the server, aborting.

sorry about the multiple threads, I didn't realize the first one had been posted, I'm new to all this

---

### Post by dcast on 2008-11-11
Try 'sudo startx' then. I don't know why you wouldn't have permissions for that though :-~

---

### Post by ozguitarplayer on 2008-11-11
then I get

x: warning; process set to priority -1 instead of priority 8 
Fatal server error:
Server is already active for display 8
If this server is no longer running, remove /temp/.x8-lock

then it goes back to the original

nigel@nigel - desktop:~$

with the cursor waiting

---

### Post by ozguitarplayer on 2008-11-11
ahhhhhh! simply type "exit" 
thanks

---

