---
title: "apt-get remove uninstalled hal, gnome-desktop and other pachages"
date: 2008-07-29
forum: General Help
---

### Post by medo_87 on 2008-07-29
Hello everyone,

I uninstalled usbutils package and apt-get removed gnome-desktop, hal and network manager in the process. I am wondering if there is a way to reinstall them without doing a fresh install of ubuntu?

I tried using the packages in the liveCD, but since hal is removed i couldn't access my CDROM drive at all, I also couldn't download them no network maneger and don't know exactly how to connect to a network from a tty.

oh btw it is at Hardy 8.04
Thanks alot for your help guys

Medo

---

### Post by PmDematagoda on 2008-07-29
Can you post the output of:-
```
cat /etc/fstab
```

---

### Post by danwood76 on 2008-07-29
You can boot up with a live CD, mount your '/' partition, chroot into that partition (mounting proc sys etc) and as long as your connected to the net you will be able to use apt-get from the terminal to install these packages.
And hopefully fix your system.

---

### Post by medo_87 on 2008-07-29
Thanks a lot danwood76. I don't know why I didn't think of doing that :p. I might come back if I get stuck somewhere

Thanks for the advice
Medo

Update: I have followed danwood76 advice and managed to get my system back to its previous state, but couldn't configure hal in the chroot environment so had to boot into tty to be able to configure it completly. 
I also noticed that I not just deleted hal and gnome-desktop but most of the main repositry by mistak. Should be more carefull in the future :p

---

