---
title: "New Install"
date: 2008-12-28
forum: Installation &amp; Upgrades
---

### Post by harddriver on 2008-12-28
I'm very new to Ubuntu.  I downloaded and installed.  Everything was fine until I updated.  Now instead of a GUI, I have a text based OS.  What went wrong??  There was 208 updates.  Help!

---

### Post by midnightfox2 on 2008-12-28
The 208 updates are normal. But what did you do to get into text based OS ?

---

### Post by pastalavista on 2008-12-28
Reboot and if it is still text mode, reboot again and select "recovery" mode (second boot option) and select "repair X".

---

### Post by harddriver on 2008-12-28
I did the updates and restarted.  When it restarted, it was in text, not gui.  It looks like the terminal.  It even asks for my sign on.  I tried pastalavista's suggestion, but the options I have do not include repair x.  My options are...

[LIST]
[*]resume
[*]clean
[*]dpkg
[*]fsck
[*]root
[*]xfix
[/LIST]

I tried the xfix to no avail.  :(

The mode I selected was "Ubuntu 8.10, kernel 2.6.27-9 generic (recovery mode)

---

### Post by pastalavista on 2008-12-28
I'm wondering if perhaps you installed Ubuntu server edition. It doesn't come with a GUI. If you have internet access try:```
sudo apt-get install ubuntu-desktop
```

---

### Post by harddriver on 2008-12-28
> **pastalavista said:**
> I'm wondering if perhaps you installed Ubuntu server edition. It doesn't come with a GUI. If you have internet access try:```
sudo apt-get install ubuntu-desktop
```

I tried that and this is what I got...


```

Reading package lists...Done
Building dependency tree
Reading state information...Done
ubuntu-desktop is already newest version
0 upgraded, 0 newly installed, 0 to remove, and 0 not upgraded

```

---

### Post by harddriver on 2008-12-28
OK.  The problem lies in the graphics driver.  I have 2 Nvidia 7600GT Fatal1ty's NOT running SLI.  I cleared the HD and reinstalled Ubuntu and then installed the recommended graphics driver.  It then told me to reboot.  Upon reboot I have the command line interface instead of the GUI.

---

### Post by namdung on 2008-12-29
In Terminal
```
startx
``` to start an x server.

---

### Post by harddriver on 2008-12-29
I'm not wanting the server version.  I am using desktop version.  I need to rollback the graphics driver.  If I can do that I am confident that the OS will start with the GUI.  OK, how do I do that?

---

### Post by harddriver on 2008-12-29
Could someone tell me how to roll back the graphics driver so I dont have to do another reinstall?

---

### Post by pastalavista on 2008-12-29
x server is the graphics adapter configuration. try what namdung said. are you using 64 bit version? how about a printout of ```
lshw
```

---

