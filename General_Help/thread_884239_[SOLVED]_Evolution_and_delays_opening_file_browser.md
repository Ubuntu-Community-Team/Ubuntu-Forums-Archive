---
title: "[SOLVED] Evolution and delays opening file browser to save attachment"
date: 2008-08-08
forum: General Help
---

### Post by bruban on 2008-08-08
I'm finding a mildly annoying problem that has cropped up with Evolution under Ubuntu 8.04.


When I try to save an attachment in Evolution and press either the save or save as button, I find that I have to wait an average of 25 seconds for the File Manager dialog box to appear.

Can anyone suggest a way to reduce this delay.


The plaform is on a Dell Pentium 4 2.4 GHz PC.

I have my home and data directories mounted via nfs from a Debian 4 server. There is a gigabit LAN connection between the server and PC with minimal activity. I have no other network problems and Nautilus works fine accessing data from the nfs shares.


Evolution is connecting to my local mail server via IMAP. The mail server has been stable for at least eighteen months. 

This problem was not present with previous versions of Ubuntu on the same desktop PC accessing the same server (configuration has not changed).

Any ideas?

---

### Post by linuxuser42 on 2008-08-22
FYI: Our installations have this 'save'-delay also after we began using Ubuntu 804. Very frustrating.

---

### Post by bruban on 2008-08-22
I've found that it is not just Evolution.

I'm experiencing the same problem with Open Office.

---

### Post by linuxuser42 on 2008-08-22
... and firefox + gedit

---

### Post by linuxuser42 on 2008-08-22
And it is something in gnome. 
Changing the window manager to e.g. icewm makes the problem disappear.

---

### Post by linuxuser42 on 2008-10-23
Found out that my problem was related to tracker. 
Disabling tracker and tracker applet under System->Preferences->Session made the problem go away. 
If I were a tracker user this was a problem. Wonder why gtk programs are implicitly tied-up with tracker.

---

### Post by bruban on 2008-10-24
Excellent!

This fixed my problem too.

Thank you for the tip.

---

