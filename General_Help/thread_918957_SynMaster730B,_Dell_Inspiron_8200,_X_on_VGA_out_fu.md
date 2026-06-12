---
title: "SynMaster730B, Dell Inspiron 8200, X on VGA out funky"
date: 2008-09-13
forum: General Help
---

### Post by octoberdan on 2008-09-13
Recently I broke my laptop's LCD screen forcing me to use an external monitor. However, when I startx (or try to start GDM) the display gets all funky. By this I mean that everything is blury, the colors are off, and all that resembles a desktop is a big giant offset image of a folder (a folder in /Desktop).

My laptop is a Dell Inspiron 8200
The monitor is an SyncMaster 730B (a Samsung LCD)

My xorg.conf looks very vanila without any numbers or specific configurations. How would I post this from my terminal? It would be a chore switching between links and emacs typing up the configuration. Anywhere I can ftp the file or something?

startx shows no failures
dmesg shows no failures, errors, or warnings
I've dpkg-reconfigured xserver-xorg and xorg
I've removed and reinstalled xserver
Display was fine on laptop's LCD (before I stepped on it)
I have never tried to use an external monitor before

lspci shows that I have a "VGA Compatible Controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)"

Any suggestions as to how I can further diagnosis this issue or any input what so ever would be greatly appreciated. 

Thank you!

---

