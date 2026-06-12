---
title: "Unable to boot"
date: 2008-11-13
forum: General Help
---

### Post by lcruz007 on 2008-11-13
Hello,

I was upgrading from Ubuntu 8.04 LTS to 8.10, my internet is not so fast, so left it all the night downloading the packages. 
When I checked on the morning, I wasn't able to boot the OS... "Could not start the X server (your graphical environment) due to some internal error). If I try the recovery mode, in terminal, I cannot use sysres...! When I check for restore points, it says that restore points does not exist. 

What can I do???


Thanks in advance

---

### Post by porchrat on 2008-11-13
Try this...it is the holy grail of saving people's x-servers.

```
dpkg-reconfigure xserver-xorg
```

Of course you will need to load into a shell.  So when it tells you it can't load the x-server press ctrl+alt+F1 to get to a shell with a loging prompt.  Then login (with your normal username and password) and run the above command...hopefully that will help.

---

### Post by lcruz007 on 2008-11-13
Well, I reinstalled Ubuntu because I needed it asap. Lost some configurations though...

But this will surely be helpful for future reference. :)

Thank you!

---

