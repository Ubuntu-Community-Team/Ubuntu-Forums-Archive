---
title: "X-server not working after upgrade ubuntu 9.04"
date: 2009-07-24
forum: Installation &amp; Upgrades
---

### Post by jeherul on 2009-07-24
I have install ubuntu-9.04 (from ubuntu-9.04-dell-reinstall dvd) in Dell Studio 1555 laptop and Its working fine . But after i update it through synaptic packet manager and rebooted the X server is not working . It works in recovery mode but without graphics .

Please help ...

---

### Post by wojox on 2009-07-24
Did you try :

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jeherul on 2009-07-24
Thank you for reply . 

I just tried this but not working .... 

I go to Ubuntu recovery mode and chose the shell prompt and tried this cmd.After i rebooted the system and start in normal mode but just only a blinking screen come .

 I have ATI Radeon 4570 Graphics card in my laptop .

---

### Post by wojox on 2009-07-24
Choose recovery mode. when it gets to the menu, choose the "x fix" option.

---

