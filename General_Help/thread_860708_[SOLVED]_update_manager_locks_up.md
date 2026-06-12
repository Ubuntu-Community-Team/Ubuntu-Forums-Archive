---
title: "[SOLVED] update manager locks up"
date: 2008-07-15
forum: General Help
---

### Post by vegypete on 2008-07-15
when i go to the update manager or when i try to add new software, i am not being asked for my password as used to happen. the application then just sits there doing nothing and i have to restart ubuntu to get rid of it.

---

### Post by iaculallad on 2008-07-15
> **vegypete said:**
> when i go to the update manager or when i try to add new software, i am not being asked for my password as used to happen. the application then just sits there doing nothing and i have to restart ubuntu to get rid of it.

Had you tried using the terminal instead to install the updates?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by vegypete on 2008-07-15
thankyou. i was able to run the update with apt as you suggested. it asked for my password. this seems to be the problem with the gui, as i am not being asked for the password there.

---

### Post by iaculallad on 2008-07-15
Or could try using the gksudo command to get to Update Manager:

```
gksudo update-manager
```

---

### Post by vegypete on 2008-07-15
it appears that the administrative application, whatever that is, won't start. it shows at the bottom of the screen for a while and then gives up.

---

### Post by iaculallad on 2008-07-15
Try installing the policykit if it could help:

```
sudo apt-get install policykit policykit-gnome
```

---

### Post by vegypete on 2008-07-16
Thank you for your help.
Found solution at thread -  [SOLVED] Problems with starting administrative applications in 8.04 .
It was all to do with the network host as explained in that post.

---

