---
title: "how to get compiz in ubuntu 8.04 under wubi"
date: 2008-08-05
forum: General Help
---

### Post by Dark-Angel on 2008-08-05
Hi i just installed ubuntu 8.04 under wubi and trying to install compiz to get effects. I tried running the command in terminal and got error that it the package wasn't found. I went into appearance properties and went to change it to normal and got popup that it couldn't be enabled. Under hardware drivers i have nividia with tick in enabled and not in use next to it. ANything i can do to get compiz?
thanks

---

### Post by Hyper Tails on 2008-08-05
have you tried this code?

```
sudo apt-get install compizconfig-settings-manager emerald fusion-icon
```

try installing envy
```
sudo apt-get install envyng-gtk

```Hope this helps you :)

---

### Post by prototype_angel on 2008-08-13
What graphics card do you have?

If it asks for install of a restricted driver (nvidia, ati), then compiz should start automatically.

You can also go to system->Preferences->Appearence and change the "desktop effects" to high, which should give you the kind of effects that you see on youtube.

---

