---
title: "Problem With GUI (GDM, KDM, XDM)"
date: 2008-09-10
forum: General Help
---

### Post by matey3 on 2008-09-10
Hello All:
I just setup my Ubuntu 8.04 hardy Server but unlike Feisty 7.04 which I had before this one cannot run any GUI (or X) program/interface?
The message I get (even after rebooting) is that "...gdm[6391]:Warning: GDM is already running..Aborting"... 

So I looked for it by Alt F7 and I only see a blinking cursor and a black screen there?!
Is there a configuration file that I should be running before running gdm? I thought the first time you ran the X, the config. screen would come up (to set the screen res and detect hardware etc.)?
Any clue?

Thanks!

---

### Post by unca.paka on 2008-09-10
The Server editions dont come with a desktop enviroment installed by default, you have you install X, and then whatever wm you want(gnome, kde, flux, etc...) Search around in the forums, theres a few howto's floating around to get you started.
Plus, you could also just install the desktop version of hardy, unless you actually need a full-fledged server that it.

---

### Post by hyper_ch on 2008-09-10
why did you install the server edition?

---

### Post by Vivaldi Gloria on 2008-09-10
In terminal give the commands:

```

sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
```

and restart using the command

```
sudo reboot
```

---

### Post by matey3 on 2008-09-10
> **unca.paka said:**
> The Server editions dont come with a desktop enviroment installed by default, you have you install X, and then whatever wm you want(gnome, kde, flux, etc...) Search around in the forums, theres a few howto's floating around to get you started.
Plus, you could also just install the desktop version of hardy, unless you actually need a full-fledged server that it.

Thanks a lot!


> **hyper_ch said:**
> why did you install the server edition?
well to tell you the truth I had No luck with the Desktop edition bcs I tried it first then I thought since my last Feisty 7.04 server worked so well I could use the Server edition again!?
I messed my feisty up when I did an upgrade (one of those auto updates) went half way and gave some errors (like it couldnt replace some files bcs they were being used duh? and so the next time I rebooted the GUI was Gone...



> **Vivaldi Gloria said:**
> In terminal give the commands:

```

sudo dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
```

and restart using the command

```
sudo reboot
```

Great Help.. Thanks a lot!
I think that is what I need...
And sorry for late reply...

---

### Post by Sycron on 2008-09-10
To start GDM you can just use ```
sudo gdm
```.

---

### Post by matey3 on 2008-09-10
> **Sycron said:**
> To start GDM you can just use ```
sudo gdm
```.

Thank you as well...
I appreciate the info very much cuz I am pretty new to Ubuntu.
Used to do a little redhat way back..
any ways I figured out how to get rid of sudo for everything...

but I guess everyone already knows how to login as root but want to be safe?! I didnt and see where I am now? ;)
lol
:)

---

### Post by Sycron on 2008-09-11
You can't be safe while running root account.

---

