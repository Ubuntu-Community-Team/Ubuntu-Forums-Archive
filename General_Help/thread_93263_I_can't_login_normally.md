---
title: "I can't login normally"
date: 2005-11-21
forum: General Help
---

### Post by detyabozhye on 2005-11-21
I was canging permissions on some of my files in my home directory using Konqueror (Nautilus doesn't do such a good job at this), and it crashed my system. Now when I log in, it tells me my session lasted less than 10 seconds and when I hit ok, it logs me back out. I can only log in with fail-safe termial, and launch gnome-panel, nautilus, and metacity from the terminal, and then use my system. How can I recover it so I can login normally every time? One of the error lines says it failed to create X11(and some more numbers I think).

---

### Post by steve.horsley on 2005-11-21
Fitst off, try deleting the file .ICEauthority in you home folder.

If that doen't work, as root, rename your home folder to something else and make a new empty home folder for yourself. This should let you start x properly again. then drag your files back into the new home. Like this:
sudo mv /home/steve /home/steveX
sudo mkdir /home/steve
sudo chown steve:steve /home/steve

HTH
Steve

---

### Post by SuperDiscoMachine V.5.7-3 on 2005-11-21
To clarifiy it a bit more: at startup, you need to select option #4 (I believe) "Fail-safe Terminal". After you logged in, you can remove the .ICEauthority file. I had this problem yesterday, after removing the file and restarting, I could normally log in again without any trouble.

---

### Post by detyabozhye on 2005-11-21
Thanks, I'll try that as soon as I get something printed here.

---

### Post by detyabozhye on 2005-11-21
Thanks, it works great now.

---

