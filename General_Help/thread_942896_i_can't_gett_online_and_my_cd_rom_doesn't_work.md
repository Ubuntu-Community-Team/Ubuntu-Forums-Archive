---
title: "i can't gett online and my cd rom doesn't work"
date: 2008-10-09
forum: General Help
---

### Post by Manden08 on 2008-10-09
hi i am very new to ubuntu, i've installed it inside windows and i am having trouble getting online, and my dvd drive is not working, it seems as though i need to install drivers but how can i do this if i cannot get online and use my disk drive.  although i do believe my flash drive works so i can use that but where do i get the drivers?  someone please help

---

### Post by DrSantos on 2008-10-10
Is your dvd drive usable in general (e.g, windows)?
How are you connecting to the internet: wireless, ethernet?
Do you mean you are dual booting by "installed it inside windows"?

---

### Post by Manden08 on 2008-10-17
i have it duel booted so i can get online using windows, also i can use my other computer.  my internet connection is wireless or ethernet, and i have tried both with no success

---

### Post by jerome1232 on 2008-10-17
I take installed in windows to mean you used wubi (Where you install from within windows, and Ubuntu can be removed as if it was just a regular windows program)

Well lets go after the internet first. Wired.

When you plug the ethernet cable in can you try these commands and post the output.

```
ifconfig
```
might want to try eth1 as well depending
```
sudo dhclient eth0
```

---

