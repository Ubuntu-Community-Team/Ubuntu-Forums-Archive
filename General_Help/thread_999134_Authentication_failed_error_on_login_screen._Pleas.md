---
title: "Authentication failed error on login screen. Please help!"
date: 2008-12-01
forum: General Help
---

### Post by Hartbuntu on 2008-12-01
I installed a program(from synaptic) that would unlock my keyring on login as long as my password and the keyring were the same. I think the program's name was pam. I needed to unlock my keyring on login so i didn't have to every time I booted up so i can connect to the internet. Because i had my settings to automatically sign me in, the keyring would not unlock. I changed the settings to not auto log me in and when i rebooted, the login screen came up, but a notification popped up saying "Authentication failed". I tried pressing ok but immediately another one saying the same thing came up. this happened continually and even after rebooting again, the same thing happened. i now do not have access to my computer to uninstall pam or change the settings back. Is there any way that i can access a terminal on my computer remotely or change the settings back remotely? I am running ubuntu 8.10. Thanks, and all help appreciated very much.

---

### Post by HalPomeranz on 2008-12-02
<Ctrl>-<Alt>-<F1> will let you access a text-mode console on the system (<Ctrl>-<Alt>-<F7> to get back to the GUI).  Not sure exactly what you're going to need to do to recover the system once you're logged into text mode, but at least you'll be able to get access.

---

### Post by deeaycee on 2008-12-16
Same issue fixed with with this post...

[http://ubuntuforums.org/showpost.php?p=3605925&postcount=4]("http://ubuntuforums.org/showpost.php?p=3605925&postcount=4")

(from login screen do a alt + ctrl + f2)

```
sudo nano /etc/pam.d/gdm
```

remove this line

```
@include common-pamkeyring
```

---

