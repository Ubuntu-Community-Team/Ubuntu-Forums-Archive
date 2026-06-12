---
title: "Wacom Bamboo Top buttons (xf86-input-wacom-0.19.0)"
date: 2013-01-14
forum: Hardware
---

### Post by BoudewijnD on 2013-01-14
Hi,

I wanted to hookup my old wacom bamboo (MTE-450) to my machine (Ubuntu 12.04). However I found out that I could set only the bottom 2 buttons and the wheel. The top two buttons I was unable to set using xsetwacom, because buttons 8/9 are not allowed.
I found [this]("http://old.nabble.com/-Arch-Linux--Wacom-Bamboo-MTE-450-Tablet%3A-can't-set-arrow-buttons-(Button-2-and-4-)-td34084585.html") post. Here the suggestion was made to upgrade the xf86-input-wacom-0.19.0. so I did. But after a reboot my machine would not start the Ubuntu only the terminal, but when I unhooked the tablet it would boot like normal. However when I reconnect my Wacom the whole system freezes and a hard reboot is the only solution.

Did I miss something or do  need to upgrade a other package?

\BoudewijnD

---

### Post by Favux on 2013-01-14
Hi BoudewijnD,

For Precise you have to apply the frankenserver patch to xf86-input-wacom.  See:  [http://ubuntuforums.org/showpost.php?p=12374240&postcount=1081](http://ubuntuforums.org/showpost.php?p=12374240&postcount=1081)  I haven't done the update for input-wacom-0.16.0 and xf86-input-wacom-0.19.0 yet, but other than the versions the instructions are the same.

---

