---
title: "Help!!!!!"
date: 2008-07-28
forum: General Help
---

### Post by Xpictoc on 2008-07-28
Ok, so I logged into Ubuntu today and it said 'cannot resume image' or something along those lines, and boots me directly into the tty terminals and not into X......ctrl + alt f7 does nothing to get me into the gui....nothing against the command line but I'm not that l33t to enjoy doing everything in it...I need to get back into X!!!......I think what might have happened was I installed KDE4 to see what all the hype was about, didn't like it as much as gnome, went back to gnome, and for some reason it wants to log into the KDE4 login screen but since its not there logs me into tty.....hmmm this might not be the reason, but I really need some help!

---

### Post by tamoneya on 2008-07-28
try typing this:```
sudo dpkg-reconfigure ubuntu desktop
sudo /etc/init.d/gdm start
```

---

### Post by Xpictoc on 2008-07-28
Hmmm....and If it is like I suspect....do I have to reinstall KDE4 to get the login to work, or is there a command I can use to switch to gnome login.......Please someone I need help...cannot deal with windows much longer.......too much loading......slowly.......loading...........data..............

---

### Post by Xpictoc on 2008-07-28
THANK YOU!!!! Very fast reply you are the man!

---

### Post by Xpictoc on 2008-07-28
:'(....so I logged out of windows, and back into ubuntu......did the fix listed above and for the first command it told me "Ubuntu is not installed nothing reconfigured" or something similar to that....second command..."Gnome is not the default login" or similar.......I'm so sad that I have to reboot into ubuntu again because if it doesn't work again I have to take the 5 more minutes to log back into windows!!! urg!

---

### Post by tamoneya on 2008-07-28
okay so apparently while messing with KDE you uninstalled gnome.  Here is the fix:```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure ubuntu-desktop

```
Then try giving it a restart.

If you again want to try something out and arent really sure what you are doing a nice strategy would be to use the live CD.

---

### Post by ajgreeny on 2008-07-28
My suspicion is that your install of kde4 had meant that kdm is now the default instead of gdm.  I somehow doubt that you uninstalled all of gnome, though that is possible, I suppose.  However try```
 sudo dpkg-reconfigure gdm
```in terminal or even in the console if needed.  This will possibly give you the choice of two and allow you to choose gdm again.  If it just says "Reloading gdm" then I am lost, but let's hope!

---

