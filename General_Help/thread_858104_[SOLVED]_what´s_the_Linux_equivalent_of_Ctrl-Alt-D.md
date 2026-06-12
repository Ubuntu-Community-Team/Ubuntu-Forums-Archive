---
title: "[SOLVED] what´s the Linux equivalent of Ctrl-Alt-Del Task Manager"
date: 2008-07-13
forum: General Help
---

### Post by charonred on 2008-07-13
What´s the equivalent command in Linux to bring up a ¨Task Manager¨ to kill a non-responding application?

---

### Post by sayakb on 2008-07-13
When an app becomes unresponsive in linux, the rest of the programs work just fine, unlike windows. So just click on the program's close button (or type **killall appname **at a terminal) and press Force Quit when prompted to. You may also add the System Monitor applet (equiv of Windows Task Mgr). Right click on panel, click **Add to panel** and add the **System Monitor** applet.

---

### Post by rraj.be on 2008-07-13
you can use system monitor to do these things.
```

System --> Administration --> System monitor.
```

---

### Post by Stacks on 2008-07-13
System > Administration > System Monitor pick the Process tab hi light
the the app pick the end process button.:popcorn:

---

### Post by cyclobs on 2008-07-13
anyway of assigning that app to something like 'ctrl+alt+del'?

---

### Post by Steveway on 2008-07-13
Press ctrl-alt-esc and click on the app you want to close after the cursor changed.
This command initiates xkill, at least here on my xfce-box.

---

### Post by cyclobs on 2008-07-13
> **Steveway said:**
> Press ctrl-alt-esc and click on the app you want to close after the cursor changed.
This command initiates xkill, at least here on my xfce-box.

doesn't work for me here on gnome

---

### Post by Rhubarb on 2008-07-13
To run xkill in gnome:
Press Alt + F2, type in xkill and press enter.  It's not quite as nice as Xfce and KDE's ctrl + alt + esc method.
I'm sure there's many other ways to get xkill running easily :)

---

### Post by charonred on 2008-07-13
Hey thanks everyone, I&#314;l make a note of the answer/s

---

### Post by jonlemur on 2008-07-13
I haven't tried it personally, but I would imagine you could use xbindkeys to run xkill from (nearly) any arbitrary button combination.

---

### Post by dracayr on 2008-07-13
you can also:

right click on panel -> add -> Force Quit

you really won't need a butten combination

dracayr

---

### Post by txcrackers on 2008-07-13
In KDE, if you press CTRL+ESC, you get the KDE System Guard process table, which is essentially the same thing as the process list in Windows' Task Manager.

---

### Post by pcjunkie on 2008-07-13
> **dracayr said:**
> you can also:

right click on panel -> add -> Force Quit

you really won't need a butten combination

dracayr



The easiest thing around really. Works like a charm :)

---

