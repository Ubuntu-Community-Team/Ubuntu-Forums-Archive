---
title: "No sound after playing Americas Army"
date: 2008-08-25
forum: General Help
---

### Post by artti on 2008-08-25
There's no sound after playing Americas Army. I have to do restart to get sound back.

Any solution!?

---

### Post by Ryadt on 2008-08-25
Try ```
sudo killall pulseaudio
```

---

### Post by Crafty Kisses on 2008-08-25
If kill Pulse Audio doesn't work, post the results of > lspci

---

### Post by artti on 2008-08-25
> **Ryadt said:**
> Try ```
sudo killall pulseaudio
```

Well that didn't help, but it gave me idea search something similar and i killed armyops-bin, which solved my problem. 

Thanks.

---

### Post by Uber-Nut on 2008-10-25
[B][SIZE="2"][FONT="Franklin Gothic Medium"]I've dealt with this problem as well. A way to automate the process is to create a custom launcher.[/FONT]
[/SIZE][/B]
[B][I]There are two ways to create a custom launcher.
[/I][/B]
[SIZE="2"][FONT="Arial"]Right-Click on a Panel and select '_A_dd to Panel' from the menu.
At the top of the window that appears select 'Custom Application Launcher'
[/FONT][/SIZE]
**OR**

[SIZE="2"][FONT="Arial"]Right-Click the Desktop and select 'Create L_a_uncher...'
[/FONT][/SIZE]

Name the launcher whatever you decide to and copy this into the 'Comm_a_nd' text box:
```
killall -9 armyops-bin
```

Select an easily recognizable icon for the launcher and add a description as you see fit.

Click the launcher to 'free up' your sound device after exiting America's Army.
Happy Fragging!:razz:

---

