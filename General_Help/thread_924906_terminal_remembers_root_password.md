---
title: "terminal remembers root password"
date: 2008-09-20
forum: General Help
---

### Post by yazifeather on 2008-09-20
I have an issue with terminal and specifically sudo. When I first log in and ask for anything that requires root access I use sudo and it asks me for the pass as it should. However once I have done this once while logged in sudo no longer asks me for my root pass when I use it. The whole concept of if I have done anything with sudo that anyone could come by (if I had not logged out) and have complete access to my computer through sudo without it asking for password is rather disconcerting. 

Thank you for your help.

---

### Post by mb_webguy on 2008-09-20
By default, sudo (and gksu as well) have a 15 minute grace period before you are asked for your password again.  You can decrease this time if you want.  Check out [this page]("https://help.ubuntu.com/community/RootSudo") for more info, and [this one]("http://ubuntuforums.org/showthread.php?p=116697#post116697") for info about how to decrease the timeout.

---

### Post by iaculallad on 2008-09-20
After inputting your sudo password, you can directly clear it by:

```
sudo -k
```

This command removes the your time stamp for the sudo command, thus making it expired.

For more info:

```
man sudo
```

---

### Post by yazifeather on 2008-09-20
Ok thanks for that information :) I will look into shortening it.

Edit: I made this post before seeing the second reply and I will look into that as well.

---

