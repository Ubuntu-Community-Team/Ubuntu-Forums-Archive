---
title: "nvidia graphics problems"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by jdakar on 2009-02-26
I am new to Ubuntu and have searched for answers for weeks now. I have a MX 440 card. When I use Linux free drivers I get an odd resolution for my card. When I use restricted drivers I can get the right resolution and it identifies my monitor, but only till I reboot. When I reboot I get either no screen or one that just flashed with aal sorts of colors. I have tried Envy and get the same results. Also when I try to change visual effects from none to normal I get a white screen and then it reverts back to none. I will continue my search for an answer, but would really appreciate help from anyone who may have an answer. What I see of Ubuntu I really like and do not want to give up on it. But I like to play games and really need 3D graphics to work.

---

### Post by smani on 2009-02-26
You could try to manually install the latest drivers - grab the one you need from [http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606), then proceed as follows:
- switch to virtual terminal, CTRL+ALT+F1
- stop the graphical user interface: sudo /etc/init.d/gdm stop
- cd to the directory where you have downloaded the file
- chmod +x filename (set it as executable)
- sudo ./filename (run the installer)
- follow the instructions, let it automatically configure the x server in the end.
- sudo /etc/init.d/gdm start to restart the graphical user intefrace

NOTE: if you install the driver manually, then likely after you update the kernel the graphical user interface will fail to load - you will have to repeat the procedure.

---

### Post by jdakar on 2009-02-27
Thanks for the help, but it didn't work. It can't be THIS hard to install drivers...can it? I got an error that says "No precompiled Kernel interface found to match your Kernel" and later another one that says "You do not appear to have libc header files installed". I don't even know what those are! I searched the internet for them and couldn't find anything about them.

---

