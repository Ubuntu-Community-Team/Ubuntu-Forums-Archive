---
title: "hardy orange loading screen(booting GUI)"
date: 2008-08-12
forum: General Help
---

### Post by naresh6188 on 2008-08-12
hi guys,
i'm not able to see the boot screen instead a black screen till the login window appears, plz help me how to enable boot screen again.....

thanks in advance.

---

### Post by Canis familiaris on 2008-08-13
Hello

Open up the terminal and Issue these commands

```
sudo update-alternatives --config usplash-artwork.so
```
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

Keep in mind DO NOT CLOSE THE TERMINAL during the execution of these processes.

Hope that helps.

P.S. Also it is advisable not to start two threads on the same topic

---

