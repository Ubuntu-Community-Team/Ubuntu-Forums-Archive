---
title: "Upgrade to Jaunty=no gnome session"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by ministoat on 2009-04-23
upgraded from 8.10 to 9.04 earlier, and now gnome doesn't seem to start! 

I can't remember the exact error, but I get a message saying that my gnome session lasted for less than 10 seconds, with a long reel of errors ending saying that gconf couldn't start or be found..

I tried starting a gnome failsafe session but this just hangs, any ideas what I can do to fix this?

---

### Post by khelben1979 on 2009-04-23
No, but you can always install KDE in the meantime so that you have a working graphical enviroment, at least.

```
sudo apt-get install kde
```

---

### Post by ministoat on 2009-04-24
I think what the problem might actually be is that my grub menu.lst is on another partition..if anyone is reading this could they post their jaunty grub menu.lst file? :)

---

### Post by ministoat on 2009-04-24
actually there's no jaunty kernel anywhere on my system!  here's more about the error message though:

It seems the xsession cannot start..

"Xlib: extension "Generic Event Extension" missing on display  ":0.0".

"gm session cannot create /dev/null: Permission denied"


I can't seem to boot to any of my ubuntu kernels, just into linux mint now :/

---

### Post by ministoat on 2009-04-24
bump :O

---

### Post by pbhj on 2009-04-24
I had that [Xlib error whilst updating]("http://alicious.com/2009/ubuntu-upgrade-intrepid-to-jaunty/") but not the /dev/null issue. The Xlib error doesn't appear to have manifest as an issue now I'm running Jaunty however.

What do you mean by "there's no jaunty kernel on my system", what's the output of "uname -a" ? Does "update-manager -d" show that you've upgraded or not??

---

### Post by ministoat on 2009-04-24
I can't log onto my ubuntu install - i've been dual booting with linux mint, and my active grub file is on that partition.

I can't find a jaunty kernel image to boot from on my ubuntu partition, if that makes sense?

---

