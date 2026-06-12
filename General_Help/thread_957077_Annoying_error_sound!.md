---
title: "Annoying error sound!"
date: 2008-10-23
forum: General Help
---

### Post by Shiv4m on 2008-10-23
Does anyone else get that annoying error sound when you backspace when theres nothing to backspace? How can I disable that or change it?

---

### Post by geirha on 2008-10-24
Unload the pcspkr module. 

Running this in a terminal will disable it until next reboot
```
sudo modprobe -r pcspkr
```

To have the pc speaker disabled permanently, add this line to /etc/modprobe.d/blacklist
```
blacklist pcspkr
```

EDIT: Oh and an easier solution is to disable it just in gnome-terminal by choosing Edit -> Active Profile, and then disable the terminal bell.

---

### Post by Shiv4m on 2008-10-24
Your a God, thank you so much.

---

### Post by Shiv4m on 2008-10-26
How do I get rid of that awful sound forever?

---

### Post by geirha on 2008-10-26
> **Shiv4m said:**
> How do I get rid of that awful sound forever?

By blacklisting the pc speaker module so it doesn't get loaded automatically when you boot ...

> **geirha said:**
> 
To have the pc speaker disabled permanently, add this line to /etc/modprobe.d/blacklist
```
blacklist pcspkr
```


---

### Post by Shiv4m on 2008-10-27
I tried writing blacklist pcspkr to terminal and it says "bash: blacklist: command not found"

---

### Post by geirha on 2008-10-28
You do ```
sudo gedit /etc/modprobe.d/blacklist
``` And then add the "blacklist pcspkr" line at the bottom of that file. After next reboot, the PC speaker should be nice and silent.

---

### Post by pholden on 2008-10-28
You can click *System -> Preferences -> Sound -> System Beep* and then untick the *Enable system beep* preference.

---

