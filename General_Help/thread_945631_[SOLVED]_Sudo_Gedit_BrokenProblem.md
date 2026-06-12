---
title: "[SOLVED] Sudo Gedit Broken/Problem"
date: 2008-10-12
forum: General Help
---

### Post by joeyknuccione on 2008-10-12
When trying to edit my xorg.conf file, I use..

sudo gedit /etc/X11/xorg.conf

When doing this it is way slow, and it locks up. I'm unable to modify the settings (my nvidia can't modify them either). The only way out of gedit is to force quit. How can I fix this? Preciate any help.

---

### Post by sisco311 on 2008-10-12
try:
```
gksu gedit /etc/X11/xorg.conf
```
(for graphical application use: gksu or gksudo)

Post the error message if you get one.

---

### Post by forger on 2008-10-12
Disable all your plugins

also try:
```
gksu gedit /etc/X11/xorg.conf
```

---

### Post by fooman on 2008-10-12
i don't know if it will help you with your problem,  but when editing a file by command line (like nano)...use sudo

when using a gui (like gedit)...use gksudo:

```
gksudo gedit /etc/X11/xorg.conf
```

edit:  too slow...forger beat me to it. :)

---

### Post by joeyknuccione on 2008-10-12
gksu gedit /etc/X11/xorg.conf
no go

Don't know how to disable plugins
gksu gedit /etc/X11/xorg.conf
no go

gksudo gedit /etc/X11/xorg.conf
no go


How do I disable plugins?

---

### Post by sisco311 on 2008-10-12
Can you run any other application with gksu?
for examle:
```
gksu synaptic
```

Also you can try to edit the file with nano.
nano is a text based tetx editor.

```
sudo nano /etc/X11/xorg.conf
```

Press Ctrl+o, Enter to save the file
and Ctrl+x to exit.

---

### Post by joeyknuccione on 2008-10-12
That kinda worked, so I'm marking it solved. Nvidia is still unable to write to that file, I'll start a thread on that later.

---

### Post by sisco311 on 2008-10-12
> **joeyknuccione said:**
> That kinda worked, so I'm marking it solved. Nvidia is still unable to write to that file, I'll start a thread on that later.
Try to run nvidia-settings as root from the terminal:
```
gksu nvidia-settings
```

---

