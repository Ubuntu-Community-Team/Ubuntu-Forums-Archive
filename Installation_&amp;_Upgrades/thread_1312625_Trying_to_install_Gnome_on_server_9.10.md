---
title: "Trying to install Gnome on server 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by mudcow007 on 2009-11-03
hello all 

im trying (in vain) to install a gui onto my brand spanking new install of 9.10

i have ran 

```
sudo get-apt update
```

then

```
sudo get-apt install gnome-core gdm xorg
```

after about 20mins of downloading it pulls messages up to say can not find repositories!?

any ideas (im a noob)!!

---

### Post by Topsiho on 2009-11-03
I am not sure why you should want a desktop on a server. If you want a server it probably runs better and safer without a desktop. You should then manage it in a terminal, and be able to do so.
If you want a desktop, I am not sure why you did not install a desktop. Kubuntu or Ubuntu, or whatever.

But if you still want to install Gnome on your computer, I guess (never installed a server :) ) you should, in a terminal do:

sudo apt-get install gnome-desktop-environment

I hope this helps,

Topsiho

---

