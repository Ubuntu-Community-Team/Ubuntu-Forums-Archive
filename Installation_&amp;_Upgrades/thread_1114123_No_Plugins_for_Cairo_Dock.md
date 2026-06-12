---
title: "No Plugins for Cairo Dock"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by MPTony T on 2009-04-02
Now please forgive me as im a bit of a noob with Ubuntu as a whole. My brother is the resident wizard with it and has tried to help but doesn't use Cairo Dock.

I installed Cairo Dock from the terminal. That went fine. I then went into sessions and set it to run at start-up. I then downloaded the .deb file for the plug-ins. I saved it to the desktop and ran the file. It went through the whole process and it seemed to install everything. Now when i go into the dock i cant see the applets or any of the plug-ins. I'm also running Compiz-Fusion and 8.10. Do i have to enable them or should they just start to work. My next thing (which i haven't tried) is to uninstall the dock and reinstall the dock with the plug-ins all through the terminal.

---

### Post by Mark76 on 2009-04-02
Are you using a 64 bit PC?

Because I am and I had exactly the same problem.

---

### Post by MPTony T on 2009-04-02
No i am using a 32 bit, older (5 years) HP Pavilion zv5000 with an ATI graphics card. I am going to try and wipe that stuff out tonight and install it again via the terminal. ill update.

---

### Post by MPTony T on 2009-04-03
Ok so i completely removed Cairo Dock through the Synaptic. I then:

```
gksu gedit /etc/apt/sources.list
```

added:

```
deb http://repository.cairo-dock.org/ubuntu intrepid cairo-dock
```

then:
```

wget -q http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg -O- | sudo apt-key add -
```

then:

```
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

and last but not least i ran cairo-dock in the term. I also went to sessions and made sure it was in there. Everything loaded like a champ.

---

