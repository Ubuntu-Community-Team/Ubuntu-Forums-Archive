---
title: "Preloading certain apps of my choice"
date: 2008-08-20
forum: General Help
---

### Post by agim on 2008-08-20
I would like to know how to preload some of my applications on startup. There are a couple of things that I use every time I turn on the computer. For instance, I would like to load Firefox in the background on startup, so when I use alt-f2 to start it. It loads faster. I would like to know how I can do this with any program.

I think I used to know, but I have forgotten how to do this. I think there is a config file that I can change...

Anyway, I use the basic gnome desktop.

Thanks for the help.

Andy

---

### Post by pytheas22 on 2008-08-20
Gnome has a nice GUI for configuring things to do upon login, including starting applications.  Go to System>Preferences>Sessions and click on the Startup Programs tab.  There you can add the applications that you want to start automatically.

---

### Post by forger on 2008-08-20
You must be looking for preload:
[apt://preload]("apt://preload")

> Description: adaptive readahead daemon
 preload monitors applications that users run, and by analyzing this
 data, predicts what applications users might run, and fetches those
 binaries and their dependencies into memory for faster startup times.
 .
 Note that installing preload will not make your system boot faster
 and that preload is a daemon that runs with root priviledges.


```
sudo apt-get install preload
cat /etc/preload.conf
```

---

### Post by agim on 2008-08-20
I have tried the program preload, it really didn't seem to make much difference. I let it run for about 6 weeks with little result.

Now If I run firefox on startup through Sessions. Can I make it run in the background?

---

### Post by pytheas22 on 2008-08-20
Maybe I misunderstood you the first time--are you looking to start something at system boot, before you log into Gnome?  If so, why not just [write a startup script]("strabes.wordpress.com/2006/10/16/how-to-create-a-startup-script-in-ubuntu-dapper") to call Firefox when Ubuntu boots?

I don't know of a way to make Firefox run in the background, and if you call it with an init script, root would own it.  But when you go to start Firefox with your regular user, it would probably start a lot faster because another instance would already be running.

Of course, you're not really gaining any speed here, because whether you load Firefox with an init script or with Gnome Sessions, it's going to take the same amount of time to start.

I hope this helps.

---

### Post by sdennie on 2008-08-20
You may want to have a look at [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651).  Note that I believe people have poor results doing this if preload is enabled.

---

### Post by forger on 2008-08-21
hm.. I would suggest running firefox in a tray icon using system > preferences > sessions, which will load on user login

- Firetray: [https://addons.mozilla.org/en-US/firefox/addon/4868](https://addons.mozilla.org/en-US/firefox/addon/4868)
- Alltray:
```
sudo apt-get install alltray
```

Then you simply add it in sessions, for firetray the command would probably just be:
```
firefox
```
(you have to enable start minimized)

Or with alltray:
```
alltray firefox
```

Note: Firetray 64-bit can be downloaded from [http://code.google.com/p/firetray/downloads](http://code.google.com/p/firetray/downloads)

---

