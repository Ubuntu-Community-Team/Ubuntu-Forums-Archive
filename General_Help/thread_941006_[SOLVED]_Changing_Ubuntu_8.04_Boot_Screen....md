---
title: "[SOLVED] Changing Ubuntu 8.04 Boot Screen..."
date: 2008-10-07
forum: General Help
---

### Post by icanfly0307 on 2008-10-07
[FONT="Arial"]Hi,
    I was trying to install Ubuntu 8.04 over the network a few days ago. The installation went smoothly with the exception that it was in the text-mode. When I rebooted, I found that the installer had installed Kubuntu instead of Ubuntu. I know that they are both the same distro; however, it is annoying to see the Kubuntu screen instead of Ubuntu when the computer starts up. I am a mainly Gnome based user. Does anyone know how to change the boot screen back to the original Ubuntu boot screen? Thanks for your help. :)[/FONT]

---

### Post by kabotage on 2008-10-07
open terminal and type this.   
     ```
sudo aptitude install usplash-theme-ubuntu
```
and then   
    ```
 sudo dpkg-reconfigure usplash
```

---

