---
title: "Help Computer Problems after attempt at updating"
date: 2008-07-23
forum: General Help
---

### Post by Jescrib2 on 2008-07-23
I have tried to update from gusty to hardy but was unable to.
I then ran an update through terminal. This was semi successful.
When I turn my computer on again I can no longer get to the login screen. I can see where it says ubuntu before you login but then it flashes between a black screen (sometimes there is like a green line that crosses the screen horizontally) and " Starting Timidity++ ALSA midi emulation..."
Then after a while it says "The display server has been shut down about 6 times in the last 90 seconds. It is likely something bad is going on. Waiting for 2 minutes before trying again on display :0."

Some one please help me.

I am using a Vaio VGN-FS940

---

### Post by rossjman1 on 2008-07-23
login at the command prompt and type
```
sudo dpkg-reconfigure xserver-xorg
```
Try to answer the questions to the best of your ability. Once done type
```
 gdm 
``` and the graphical logon screen should start.

---

### Post by Jescrib2 on 2008-07-23
after typing gdm I receive "warning:GDM file gdm-daemon-config-c:line 2033 (cannot run seteuid to 0: Operation not permitted" 

Screen is mean while flashing between this and a black screen with a green line.

---

### Post by rossjman1 on 2008-07-23
ok. That has always fixed these problems for me, so I don't know how to help you. However if you can post your /etc/X11/xorg.conf this would help. If you have an Ubuntu live cd you can get to that file from there. Otherwise you can use a command-line text editor such as vim and a broswer such as lynx.

---

### Post by Jescrib2 on 2008-07-23
I am unable to get the /etc/X11/xorg.conf because I do not have the live CD or those programs. Is there a way to undo the update that was done earlier today. Any other recommendation?

---

### Post by rossjman1 on 2008-07-23
sudo apt-get install vim lynx

---

### Post by retrow on 2008-07-23
> **Jescrib2 said:**
> Is there a way to undo the update that was done earlier today. Any other recommendation?
I hadn't thought about that until now. Ubuntu must be having something similar to System Restore in Windows. Now I gotta find what is. Thanks for bringing up this question.

---

### Post by Jescrib2 on 2008-07-23
Tried to install and it says "could not resolve 'us.archive.ubuntu.com'"
"Failed to fetch..."

---

