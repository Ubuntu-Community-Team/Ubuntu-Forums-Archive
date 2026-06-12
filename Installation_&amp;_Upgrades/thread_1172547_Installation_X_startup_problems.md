---
title: "Installation X startup problems"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by titoki on 2009-05-28
I am new to Linux and following a successful intall of Ubuntu on my main PC I attempted to install Xubuntu on my older machine but have some issues.
 
1) during intall the PC would hang after the location screen, eventually got around this by installing in safe video mode.  After install, did a restart and all went well.
 
2) however, after a full start from cold the startup procedure stalls after the login-in screen.  After logging in I get a light blue screen with the mouse arrow, initially there is lots of disk activity but this eventually ceases.  I can exit from here using alt:ctrl:del which gets me back to a user/swithch box and from there back to the login screen.
 
3) I can also boot up into single user mode fine but start fails.
 
4) things I have tried: 1) added things like noapci noaic no lapic etc to the startup line in grub, but no help 2) Xubuntu Live works well so looked at the xorg.conf, this was very minimal.  Found that the same xorg.conf file is used in the installed version so made a new file using Xorg -configure.  This file contain much more info so installed this as the xorg.conf file, but no help. 3) the hardware detect seems to find the right hardware eg video Trio 3D, monitor Compaq 710, etc. 4) also did a repeat full install and got the same effect ie the install goes in safe mode and directly after install everything is fine, but the problem reappears after a cold start.
 
Not sure what to do now, any suggestions/help much appreciated. 
 
Regards titoki

---

### Post by clonne4crw on 2009-05-28
If I were you, I would use the Alternate installation disk for Xubuntu. Xorg running from the LiveCD is really wonky sometimes. Once installed, you will have a better chance figuring out what the problem is, if there even is any.

---

