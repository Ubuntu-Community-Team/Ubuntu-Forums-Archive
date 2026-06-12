---
title: "Problem installing Ubuntu"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by Thinice16 on 2009-02-21
After i install ubuntu with no errors it loads up but doesnt show the loading screen and when it loads the login i login it makes the drum sound then the screen messes up and goes back to the login screen and it just keeps going back to the login screen every time i login. Any help and suggestions and greatly appreciated.

---

### Post by dzark on 2009-02-21
Sounds like its a graphics driver playing up. 

You could try (provided you're connected to wired network) pressing Ctrl-Alt-F2 to get into a text console and loging in there. Then

```
sudo /etc/init.d/gdm stop
sudo aptitude update
sudo aptitude safe-upgrade
sudo /etc/init.d/gdm start

```

Now if that doesn't work, switch back to Ctrl-Alt-F2 and let us know what it says :)

---

### Post by Thinice16 on 2009-02-21
it still does the same thing over and over again. It also freezes after i try to ctrl+alt+F2 after i try to login.

---

