---
title: "Avant Window Navigator has gone funny!"
date: 2008-09-02
forum: General Help
---

### Post by phil81uk on 2008-09-02
The attached screenshot says it all! This happened after I tried to add the ViewDesktop applet. There is a Terminal icon even though I have no terminal open. The folder icon changes the desktop image to random images.

I tried uninstall and reinstall, and rebooting.

---

### Post by anotherdisciple on 2008-09-02
Try deleting the configuration folder...

```
rm -rf ~/.config/awn
```

---

### Post by phil81uk on 2008-09-02
Hi. That didn't work.

---

### Post by phil81uk on 2008-09-03
I forgot to add, that open windows do not actually appear in my AWN. Only those two wierd icons that you see.

---

### Post by phil81uk on 2008-09-03
Well the terminal icons has gone now (dont know what I did exactly), and I removed the second icons which turned out to be an app launcher.

The only problem now is that open windows do not appear in AWN. Only applets that I add appear there.

---

### Post by anotherdisciple on 2008-09-03
hmmm.... new idea... open a terminal and type:

```
avant-window-navigator
```

It should spit out errors if something is going haywire.

---

### Post by anotherdisciple on 2008-09-03
OH... and one of the applets is in control of making a window list... I can't remember which one.

Open the AWN manager and tell me what applets you have enabled?

---

### Post by phil81uk on 2008-09-03
Some sign of life. If I do "sudo avant-window-navigator" then it works. But not if I omit SUDO.

Here is the code:

```

monkey@LII:~$ avant-window-navigator

(awn-applets-migration.py:8738): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Screen is composited.
APPLET : /usr/share/avant-window-navigator/applets/showdesktop.desktop

```

```

monkey@LII:~$ sudo avant-window-navigator

(awn-applets-migration.py:8645): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `AwnConfigClient'
Screen is composited.
LOADED : /usr/share/applications/awn-manager.desktop
APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop

```


Additionally, when I run as SUDO then it doesn't load the theme that I had installed.

---

### Post by anotherdisciple on 2008-09-04
Hmm... that is strange. I don't like running any program as Root unless if I need to.

It tries to read Root's settings instead of yours... that's why it won't use your previous theme.

I'm basically just trying to give this thread a bump because I'm just as stumped as you are.

---

### Post by phil81uk on 2008-09-05
Bump !!

---

### Post by ronnielsen1 on 2008-09-05
I had alot of probs with avant slowing down and stuff so I switched to cairo. Seems alot more stable

---

### Post by phil81uk on 2008-09-05
Correct me if I'm wrong, but the code just shows different applets being loaded. The following applet seems to be the one that actually displays tasks in AWN, and it is missing when I run without SUDO:

APPLET : /usr/share/avant-window-navigator/applets/taskman.desktop

So surely it's just a case of restoring this applet for my non-SUDO user? I just can't see this applet in the Dock Preferences. Also, the .config/awn directory is empty in both root and home/monkey. So where the heck is the configuration?

---

### Post by ellalan on 2008-09-06
Hi
I have chosen Cairo-dock as AWN was very unstable, in cairo-dock you have more choice of applets. Cairo-dock is in the synaptics and easy to install. You can tweak it to suit your taste. HTH.

---

