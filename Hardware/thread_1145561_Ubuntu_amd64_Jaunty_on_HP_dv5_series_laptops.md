---
title: "Ubuntu amd64 Jaunty on HP dv5 series laptops"
date: 2009-05-01
forum: Hardware
---

### Post by vonti on 2009-05-01
Hi, I'm experiencing multiple problems with the new Ubuntu distro update 9.04.
1. My sound card doesn't seem to work. ------> [ that thread helped a lot]("http://ubuntuforums.org/showthread.php?t=1139030&highlight=hp+dv5")
2. Compiz effects reset themselves after system reboot.
3. Films(with no sound :( ) keep breaking up.
4. Tilda program keeps reseting after restart (no key binding).
5. Emerald Theme Manager works only after writing emerald --replace in the console(which prevents me to write anything else, and resets after reboot :( )

Can anybody find me a configuration tutorial to ma HP dv5 1150ew??
Thanx anyways

---

### Post by Lenwe Tasartir on 2009-05-01
2. Have you got compizconfig-backend-gconf package?

3. Are you using Gstreamer? Which plugin is being used when you try to watch?

4. You can solve problem with Tilda by disallowing it to write its configuration.
First, clear all locks to prevent it from creating next config:
rm -f ~/.tilda/locks/*
Next, take write flag from config
chmod -w ~/.tilda/config_0

5. There is start applications tab in System -> Preferences -> Session. You can add it there. Unfortunately, I don't remember how to set default window decorator in Gnome and I can find only deprecated keys in gconf. 
> echo export WINDOW_MANAGER=compiz > ~/.gnomercMight help, but it isn't the Holy Right Way, IMHO.

---

