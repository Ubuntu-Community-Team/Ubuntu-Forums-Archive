---
title: "Ubuntu 8.10 how to enable time server: select server screen ?"
date: 2008-11-30
forum: General Help
---

### Post by esdwav on 2008-11-30
Hi there,

Does anyone know how to enable the GUI of time server in ubuntu 8.10 like Ubuntu 8.04?

[IMG]https://help.ubuntu.com/community/UbuntuTime?action=AttachFile&do=get&target=ntpgui5.png[/IMG]

[IMG]https://help.ubuntu.com/community/UbuntuTime?action=AttachFile&do=get&target=ntpgui6.png[/IMG]

---

### Post by esdwav on 2008-12-03
does anyone can help me with this?
or this is just not possible?

---

### Post by todak on 2008-12-03
Do you have ntp (network time protocol) installed? If not ```
sudo apt-get install ntp
``` from a terminal. Then go to System> Administration> Time and Date. Click on "Unlock" enter password and then select "Select Servers" and choose the server of your choice or add one in the field provided and then select it, ensuring you deselect any others.

---

### Post by esdwav on 2008-12-03
oh my goodness apparently it is there. :o
i used to access them from date panel at right top conner in ubuntu 8.04 and in ubuntu 8.10 it is not there anymore.

Thanks for replying and solving my query.

now I can do time synchronization among network. ;)

---

