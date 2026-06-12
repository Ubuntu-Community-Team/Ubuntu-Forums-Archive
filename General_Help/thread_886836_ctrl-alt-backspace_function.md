---
title: "ctrl-alt-backspace function?"
date: 2008-08-11
forum: General Help
---

### Post by cybrsaylr on 2008-08-11
Just exactly what does ctrl-alt-backspace do?

Iv'e used it a few times when 'force quit' would not work on a freeze-up. 

What is the best use for this function and is it a re-boot? It seems to correct the freeze-up and restarts faster than a full re-boot.

---

### Post by tuxxy on 2008-08-11
It restarts X, you should use when you must exit the GUI for example a system freeze.

---

### Post by OutOfReach on 2008-08-11
It doesn't reboot it just restarts the X display.

---

### Post by cybrsaylr on 2008-08-11
So it is similar to a force quit then?
Is it OK or better to use instead of force quit on freeze-ups?

---

### Post by jocko on 2008-08-11
It's ok to use, but it forces every graphical app to quit (with possible data loss in open files), not only the frozen one.
To force quit only one application, you can set up a keyboard shortcut to the command "xkill", which will allow you to just click on the applications window to kill it.
I use the "Commands" tab in the "General" settings in compiz-config-settings-manager to map xkill to the key combination Alt+X. If you don't use compiz, I don't know how it can be done, but I'm sure there is a way.

---

### Post by cybrsaylr on 2008-08-11
OK. Thanks for the responses guys.

---

