---
title: "Startup"
date: 2005-11-29
forum: General Help
---

### Post by speedy51 on 2005-11-29
How can i say to Ubuntu to start Teamspeak server when it starts?

---

### Post by matthewv on 2005-11-29
You mean when it starts or when you login..??
The former, create a symlink to the command to start the server, prefixed with S99, and place it in /etc/rc2.d/.
The latter, see System-->Preferences-->Sessions

---

### Post by detyabozhye on 2005-11-29
To add programs to startup go to System->Preferences->Sessions, Click on the Startup Programs tab and have fun.

Edit: Ahh! matthewv beat me to it, :D

---

