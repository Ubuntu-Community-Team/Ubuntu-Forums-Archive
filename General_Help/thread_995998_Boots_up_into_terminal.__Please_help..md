---
title: "Boots up into terminal.  Please help."
date: 2008-11-28
forum: General Help
---

### Post by SpikeRazorshards on 2008-11-28
Sorry guys, I screwed up.  Last night I was up real late trying to get my sound card (REALTEK ID 662) to work with 8.04 and ended up staying up til around 4 a.m. I don't remember much of what happened next, but this morning when I booted up, it all looks normal until I realize I can't load a desktop environment.  I end up logging into the shell and I stay there.  

It starts up all the processes, all ending with [OK] and then says 

```
Ubuntu 8.04.1 spike tty1

spike login:
```

And then I login and I'm stuck in the terminal. I'm hope there's a simple fix for this.  Thank you.

---

### Post by taurus on 2008-11-28
Log in with your username and password.  Then, what happens if you start X from a prompt with

```
startx
```

---

### Post by SpikeRazorshards on 2008-11-28
Thank you for the quick response taurus.  An X Session loaded up just fine, although the resolution was 800 x 640.  When I restarted, I stilled booted up into the terminal.

---

### Post by taurus on 2008-11-28
Try these.

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```

---

### Post by SpikeRazorshards on 2008-11-28
Results!  At lets I got a gui now, though I was trying to get away from GNOME by installing xubuntu.  Originally, I didn't have gdm so I had to apt-get it.  Is there any other way I can run this without having gdm now?  And now my res is at 800x640 and the only other option is 640x480.  Another challenge arises.

---

