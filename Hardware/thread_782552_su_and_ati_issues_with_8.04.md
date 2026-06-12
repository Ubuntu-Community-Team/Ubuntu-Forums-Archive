---
title: "su and ati issues with 8.04"
date: 2008-05-05
forum: Hardware
---

### Post by michaelahess on 2008-05-05
I just upgraded 7.10. sudo, and gksu no longer work. sudo gives me unable to resolve host {hostname}, and gksu just sits there until I ctrl-c it.

I also can't get compositing working with the ati driver. My AWN is broken! If I use the vesa driver, google earth and sling player run horribly.

This is a fairly clean system, I've only modified it with mac4lin. The boot screen is also corrupted color wise.

Not sure I'm liking this new version, but I'm hoping some of you guys have some ideas to fix it :)

---

### Post by Rocket2DMn on 2008-05-05
I'm not sure about your awn, but if you need to install restricted ati drivers, you can try using EnvyNG - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
For your sudo not working, you need to reboot into recovery mode kernel (since gksu doesn't work either), and run
```
nano /etc/hosts
```
Move the cursor down to the line that says something like
```
127.0.1.1	computername.somegarbage
```
delete the somegarbage part so that all that is left is
```
127.0.1.1	computername
```
It is some glitch that happens during upgrade, I had it myself, though I'm not sure where it originated.  Do CTRL+X, tell it to save the changes, then reboot normally with
```
reboot
```
You should be good to go now.

---

