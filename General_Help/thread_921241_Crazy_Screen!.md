---
title: "Crazy Screen!"
date: 2008-09-16
forum: General Help
---

### Post by jorge242 on 2008-09-16
I am a total noob and I just installed Ubuntu 8.04 (with great excitement!) along side Windows XP. When I boot into Ubuntu the screen is totally scrambled, constantly in motion. I can see the colors of the desktop. If I boot from the CD it works fine so it doesn't appear to be a driver issue. Any way to fix this? Thanks!
BTW the video adapter is ATI Radeon 9200.

---

### Post by Peter09 on 2008-09-16
This is one of those persistent problems, especially with ATI graphics card drives.
Initially go into recovery mode (ESC during boot and then select the second option in the boot menu) and try the following code at the command prompt. 
```
sudo dpkg-reconfigure -phigh xserver-xorg

```

With luck it will give you an operable screen.

---

### Post by jorge242 on 2008-09-16
I went into the Root option and tried that but it didn't work. What seems strange to me in the mouse cursor is fine. Thanks anyway.

---

### Post by Peter09 on 2008-09-16
Go into the root option again and type
```
startx
```

this may bring up a graphical GUI.

---

### Post by Promille on 2008-09-16
> **Peter09 said:**
> Go into the root option again and type
```
startx
```

this may bring up a graphical GUI.


Well, it seems like the x-server is allready running though..

---

### Post by Peter09 on 2008-09-16
The X server should not be running if you have booted straight into recovery mode. That is, selecting recovery mode from the boot menu and logging in at the command prompt.

Can you confirm that is what you are doing?

---

### Post by jorge242 on 2008-09-16
I hit esq on bootup. Second option for recovery mode. Then I get 3 more options. 1 -boot up normally, 2 -root option which allows me to type along the bottom of the screen, and 3 -i don't remember what this one was. I selected the root option. I don't know where you "log in".

---

