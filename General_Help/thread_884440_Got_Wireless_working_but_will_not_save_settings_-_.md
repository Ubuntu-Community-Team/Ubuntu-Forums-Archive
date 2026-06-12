---
title: "Got Wireless working but will not save settings - Lose on reboot"
date: 2008-08-09
forum: General Help
---

### Post by zachoeser on 2008-08-09
I finally got my wireless working - thanks to everyone who helped out....howerver
after i run the sudo modprobe -ndiswrapper and everthing works good

then i reboot

and i have to re do that entire section of steps over again... is there anyway to save this so i dont have to keep retyping that whole
sudo modprobe ndiswrapper
sudo modprobe -ndiswarpper

every time i want to use wireless

---

### Post by caljohnsmith on 2008-08-09
Zachoeser, I think what you want is:
```
sudo ndiswrapper -m
```
That creates an alias for your wlan0 interface so that ndiswrapper gets loaded (if it isn't all ready loaded) whenever wlan0 is used. That should solve your problem, but let me know how it goes for you.

---

### Post by zachoeser on 2008-08-10
i ran that code and it says everythign was already loaded . and it still will not save teh settings on reboot

---

### Post by caljohnsmith on 2008-08-10
That's not a good sign that doing that command didn't work for you, but here's another way to make sure ndiswrapper gets loaded after a reboot:
```
sudo bash -c "echo ndiswrapper >> /etc/modules"
```

---

