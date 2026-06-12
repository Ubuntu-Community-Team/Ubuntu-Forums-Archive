---
title: "desktop is all wrong!!"
date: 2008-09-12
forum: General Help
---

### Post by joe9110 on 2008-09-12
hi i turned on my pc and it seemed to boot up fine, then i came to the logon screen, still looked fine, thats until after i loged on it came up with tons of errors and the background was black and the icons were the wrong color.
the errors were like gnome power manager has not been installed properly.

please help thx

---

### Post by cdtech on 2008-09-12
If you can boot into the "recovery mode", on the command line I would start with the command:
"sudo dpkg --configure -a && sudo apt-get -f install"
Then try an update.

Hope this helps....

---

