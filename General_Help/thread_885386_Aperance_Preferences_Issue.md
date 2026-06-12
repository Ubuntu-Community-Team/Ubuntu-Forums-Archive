---
title: "Aperance Preferences Issue"
date: 2008-08-10
forum: General Help
---

### Post by p3la on 2008-08-10
When I try to the options on it from none to normal or extra all I get is a blank screen and nothing will happen unless I press escape. After that it will revert back to normal. I have an AGP X800XT 256MB I don't know if my card is too old. Any help is appreciated, thank you.

---

### Post by cdtech on 2008-08-10
Boot into "recovery mode" at the grub screen. Log in and type, at the command prompt:
```
sudo dpkg-reconfigure xserver-xorg
```

reboot into normal mode.

---

### Post by p3la on 2008-08-10
thanks for the quick reply cdtech. i tried that command and rebooted and my resolution changed, also the video driver was unticked in the hardware drivers section. i tried to do it and it still gave me a white screen, how odd. then i just renabled it and tried it again but no luck! i wonder what it could be....

---

