---
title: "Acer Extensa 4420 Battery problems"
date: 2010-12-14
forum: Hardware
---

### Post by NewUser01 on 2010-12-14
When running on battery X/Gnome hang (so did KDE, but I haven't tried that in for a few kernel updates) Currently running Kernel 2.6.35-23

If booted from battery hangs during login (just before it loads the desktop)
plugging it in unhangs it temporarily, but then it crashes and gnome has to be restarted

If unplugged during operation continues operate for a few minutes (but significantly slower)
then hangs same as if booted from battery.

KDE 4.5 worked for a while until updated the kernel, then KDE stopped working on battery, also same kernel update stopped "startx" from working.

CLI works flawlessly on battery and plugged in

It does NOT hang if you put it to sleep before unplugging, and plug it in before waking it up.

I am not sure if I should file this as a bug, or if it is my config

Any help would be greatly appreciated, thanks in advance.

---

### Post by NewUser01 on 2010-12-15
Nothing?

No thoughts/ideas

No one has a solution or no one has this problem?

Should i file a bug?

---

### Post by haudace on 2011-05-14
I had the same problem in 10.10, I also have the same laptop as yours (maybe slightly different config but who knows really?). I haven't tested my laptop on battery power after the upgrade to natty narwal ubuntu 11.04. I will try to follow this thread to see if anyone comes up with an answer.

Edit: Tested it, doesn't work, made my x hang.

---

### Post by NewUser01 on 2011-05-19
In 11.04 (and probably 10.10 as well), installing laptop-mode-tools solves the problem
```
sudo apt-get install laptop-mode-tools
```

---

