---
title: "Xubuntu Upgrade Problem"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by milawynsrealm on 2009-11-06
Right now, I have a laptop that I received from my father. It was too slow for Windows XP Home, so I decided to install Xubuntu so I could use it for my college assignments. But I'm having some problems with it. For a while now, my **GNOME Bars (the bars that you usually see on the top and bottom) are gone**. I'm lost at how to get them back (did I accidentally delete the package, or what?) and on top of that, I don't know **how to connect to the internet** in order to do the upgrades to the newest version in hope that the missing stuff will come back. Finally, when I try** to use an install CD (I even tried an alternate install) to do it, it didn't even recognize the CD and resumed normal boot-up**.

If there are any ideas on what might be the problem, then please let me know.

---

### Post by mac9416 on 2009-11-06
Howdy!

You can get the GNOME bars (actually XFCE bars in Xubuntu) back by going to the Terminal and running...

```
$ sudo apt-get install xfce4-panel  # Will fail if the panel is already installed. That's OK.
$ xfce4-panel  # Starts the panel.
$ nm-applet  # Makes sure the Network-Manager is up (so you can connect to the Net).
```

You may also try the following command, though I'm not sure what the results may be...

```
$ startxfce4  # Starts up everything that comes with xfce.
```

To boot the live CD, you may have to use a "Choose temporary boot device" key combo at the first startup screen (BIOS screen). Mine is F12. It will present you with a list of bootable devices. Simply select the CDROM drive option.

I hope all that makes sense and helps!

---

### Post by milawynsrealm on 2009-11-06
The panel seems to be running just fine, but there's still one problem. The panel seems to be dependent on the terminal window that I have running. When I close out the terminal, the panel closes out as well. I'm trying to find out if there is a way to make it so that it runs without needing the terminal.

---

### Post by sleepyjon on 2009-11-06
> **milawynsrealm said:**
> The panel seems to be running just fine, but there's still one problem. The panel seems to be dependent on the terminal window that I have running. When I close out the terminal, the panel closes out as well. I'm trying to find out if there is a way to make it so that it runs without needing the terminal.


You can hit alt + f2 to run it, or append a & to the end of the commands.

---

