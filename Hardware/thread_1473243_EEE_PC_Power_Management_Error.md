---
title: "EEE PC Power Management Error"
date: 2010-05-05
forum: Hardware
---

### Post by takumidesh on 2010-05-05
I have an EEE PC 4g with 9.10 Installed, Everything worked fine until one day i tried booting it up and i got an error saying that the configuration defaults for gnome power management did not install correctly. This error pops up on the login screen, which since the error occurred has looked very windows 2000ish.
Any help would be great, I am willing to reinstall or upgrade to 10.4 but i would prefer it if there was just a fix for this. Just ask if there is any info i may have left out. 
Thanks for any and all help!

---

### Post by mikewhatever on 2010-05-05
Can you login into the system? If not, try the recovery mode. Once logged in, try the following command:
```
sudo dpkg-reconfigure gnome-power-manager
```

---

