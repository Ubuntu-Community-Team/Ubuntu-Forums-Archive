---
title: "Warning/Error Message after login"
date: 2008-08-18
forum: General Help
---

### Post by focus310 on 2008-08-18
Hello:

When I turn on my laptop and type my username and password; the following message appears:

User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by the user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users.

What would I need to do to get rid of this message?

Thank you for the help.

---

### Post by iaculallad on 2008-08-18
On your terminal:

```
sudo chmod 700 /home/your_username
sudo chmod 644 /home/your_username/.dmrc

```

---

