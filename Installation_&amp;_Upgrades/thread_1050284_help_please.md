---
title: "help please"
date: 2009-01-25
forum: Installation &amp; Upgrades
---

### Post by connor901 on 2009-01-25
ok so i have a ubuntu desktop verison 8.10 that will boot on my laptop but when i try to boot from ubuntu server edition 8.10 it wont work and its not a bad disk because when i try to boot the server edition disk on my desktop it works.

---

### Post by taurus on 2009-01-25
When you say it won't work, what is the error message when you try to boot the CD with the server version?

---

### Post by connor901 on 2009-01-25
it will stay on a black screen for a minute or two then it will go to a screen saying stuff about like intel broadcam or something i think it just going to my network device.

---

### Post by cariboo on 2009-01-25
You do realize that the server edition has no gui. The server edition is intended to run headless, and you access it  remotely.

If you need the gui, when you get to the login prompt type your username and hit enter then enter your password, it will not be echoed back.

Next type:

```
sudo apt-get install ubuntu-desktop
```

This will install the ubuntu desktop.

Jim

---

### Post by connor901 on 2009-01-25
yea i cant even install ubuntu server edition my problem is when i insert my disk nothing happens just a black screen and its not a problem with the disk because it works fine on my desktop computer

---

