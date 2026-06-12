---
title: "Migrate to ubuntu studio"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by cjshaw on 2009-05-02
Good day all,

Quick first question. I have Ubuntu 9.04 installed on a desktop. If I want to migrate to Ubuntu-studio, how can I do this without installing from scratch?

Thanks in advance,
Chris

---

### Post by DJonsson2008 on 2009-05-02
If I understand it right Ubuntu-studio uses a special low-latency kernal,
which I'm not sure if you can upgrade to or not. The low-latency kernal is to help with DAW (digital audio). Otherwise most of the Ubuntu Studio apps as far as I know can be installed via synaptic.

---

### Post by dsavi on 2009-05-02
System -> Administration -> Synaptic Package manager. It will prompt you for your password.
When you've typed it in, type "ubuntustudio-desktop" into the quick search in the window that appears. Mark the package with that name for installation and press "Apply".

Or alternatively, open a terminal and simply execute this command:
```
sudo apt-get install ubuntustudio-desktop
```
This is probably faster, but you don't get any of those nice loading bars when it's being installed (Although you do when you download) just a bunch of scrolling text. It may take quite a bit to download the packages though, so be patient. :) Hope this helps.

---

### Post by edm1 on 2009-05-02
Just search for ubunru studio in synaptic. If the RT kernel is not installed then simply install linux-rt.

---

### Post by Partyboi2 on 2009-05-02
You should be able to install ubuntu-studio from the terminal[FONT=monospace]
[/FONT]```
sudo aptitude update && sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

### Post by cjshaw on 2009-05-02
Thanks for all the pointers. Much appreciated.

---

