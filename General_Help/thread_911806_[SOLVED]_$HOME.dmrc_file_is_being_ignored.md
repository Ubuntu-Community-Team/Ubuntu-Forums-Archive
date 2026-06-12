---
title: "[SOLVED] $HOME/.dmrc file is being ignored"
date: 2008-09-06
forum: General Help
---

### Post by Precipitous on 2008-09-06
When I boot up the computer (I am set for auto login) I get the following message box:

User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user, and have 644 permissions. User's $HOME directory must be owned by user and not writable by any other users.

If I click OK the login finishes...  Most basic functions then work fine, but I am having problems running the winetricks script (getting message that I do not own the .wine folder), so I know that not everything is OK.

Does anyone know the best way of fixing this?

---

### Post by darco on 2008-09-06
do a "search"..u will be pleasantly surprised :)

darco

---

### Post by iaculallad on 2008-09-06
On your terminal:

```
sudo chmod 644 ~/.dmrc
sudo chown your_username ~/.dmrc
sudo chmod 755 /home/your_username
sudo chown your_username /home/your_username
```

---

### Post by Precipitous on 2008-09-06
Thank you iaculallad. Problem solved!

---

