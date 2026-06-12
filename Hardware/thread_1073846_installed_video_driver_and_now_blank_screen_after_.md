---
title: "installed video driver and now blank screen after boot"
date: 2009-02-18
forum: Hardware
---

### Post by slappy95633 on 2009-02-18
ok i have a ATI x1650 pro with ubuntu 8.10 and i just downloaded the newest drivers from ati and installed them restarted the system worked fine then ubuntu came up and sayed that it needed a update (which was updates for my video card from ubuntu) it installes them i restart my computer and now after the ubuntu loading screen when it should go to sign in it just sits there with a black screen... i posted this in general help and got hardley any views and no replys so if some one could help me with this problem it would be greatly apreciated

---

### Post by teaker1s on 2009-02-19
at grub boot recovery mode and remove the driver you installed-should get you a gui back 
```
sudo reboot
```

boot as normal then
system>Administration>hardware drivers (or restricted drivers) depending on ubuntu version.
 select restricted driver and install

---

### Post by karamu on 2009-02-23
Did this work? I have the same problem- I installed drivers for my (onboard) ATI 1250 card and now I just get a blank screen after the initial boot- there's also no sound that some other people have reported so I guess it's not 100% display related? But I am no expert...... 

It's very frustrating though becuase this is a fresh installation- everything was working fine before (desktop effects and all) but I had to reinstall Ubuntu after previous problems and the problem has appeared since then.

---

