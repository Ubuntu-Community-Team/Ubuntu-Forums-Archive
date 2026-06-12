---
title: "upgrade 9.04 to 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Ofloo on 2009-10-31
What am I doing wrong. I get an error something about it can't find ubuntu-minimal

Ps you might want to add .log to the file extension list, log files should be attached.

---

### Post by phillw on 2009-10-31
> **Ofloo said:**
> What am I doing wrong.

Ps you might want to add .log to the file extension list, log files should be attached.


Not read the logs... try my blog and tell me what you did differently.

Phill.

---

### Post by Ofloo on 2009-10-31
I did read the logs .. but i can't see anything wrong also i'm not the only one with this error i was just looking through the forum and i've noticed

[http://ubuntuforums.org/showthread.php?t=1306389&highlight=ubuntu-minimal](http://ubuntuforums.org/showthread.php?t=1306389&highlight=ubuntu-minimal)
[http://ubuntuforums.org/showthread.php?t=1306323&highlight=ubuntu-minimal](http://ubuntuforums.org/showthread.php?t=1306323&highlight=ubuntu-minimal)

---

### Post by Ofloo on 2009-10-31
I think i'm going to try the disk install instead of the network install cause this seems to be an issue in the network install.. maybe this doesn't show in disk upgrades.

---

### Post by Ofloo on 2009-10-31
hah i think i found the problem, .. the issue was with the dns, .. i used be.archive.ubuntu.com which doesn't always resolve so i changed it to archive.ubuntu.com and it's still working. Haven't finished the complete installation, .. but at least it didn't stop where it stopped before.

EDIT

Ok: the install was successfull sound card didn't work but installing the asla firmware package solved that, .. 

an other thing i've noticed is that i'm not able to remove gnome-panel anymore which was the case before, .. i did sudo apt-get remove gnome-panel, i don't use it anyway so .. why should i keep it .. but this doesn't work the login will loop and prompt for a password over and over once rebooted afterwards..

---

