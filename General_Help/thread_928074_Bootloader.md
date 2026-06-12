---
title: "Bootloader"
date: 2008-09-23
forum: General Help
---

### Post by Primula on 2008-09-23
I've formatted the partition my windows used to be on, but still even though my windows is deleted the ubuntu bootloader appears and asks which os I'd like to boot, and this is annoying me. How can I make it run ubuntu straight away?.. Guess I'm a bit of a perfectionist :/

Thanks.

---

### Post by rraj.be on 2008-09-23
Follow the steps

Open the terminal

type
```

sudo grub

find /boot/grub/stage1
```

if it returns like ```
[hdX,Y]
```

type

```
root [hdX,Y]

setup [hdX,Y]

quit
```


Thats it.

It wil reinstall GRUB.

---

### Post by paulmerchant on 2008-09-23
You'll want to edit Grub's menu.lst file. Go to a terminal and type:

sudo gedit /boot/grub/menu.lst

Scroll down to near the bottom of that file and you can add a # in front of everything in the Microsoft Windows entry (or blast it). Then enjoy a wonderful feeling of complete freedom.

---

