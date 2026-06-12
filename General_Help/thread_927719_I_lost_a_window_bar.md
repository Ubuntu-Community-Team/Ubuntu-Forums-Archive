---
title: "I lost a window bar"
date: 2008-09-23
forum: General Help
---

### Post by clipse on 2008-09-23
I took a screen shot so you can see what I lost. I was trying to embed my terminal in to the desktop and in the process I lost a window bar. I followed the directions here. [http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html](http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html)

What did I do, and how can I undo it without loosing my embedded terminal?

thanks in advance. 

clipse

---

### Post by G-Dub on 2008-09-23
I think X crashed. Do you use emerald?

---

### Post by clipse on 2008-09-23
I don't think so. I hate to admit it but I've never messed with emerald. kinda new to to the whole eye candy thing.

---

### Post by vishzilla on 2008-09-23
try this command

```
metacity --replace
```

---

### Post by issih on 2008-09-23
Hmmn, I'd say that either your window manager or your window decorator has crashed.

I'm thinking the dock is awn, so presumably compiz is still up and running, so I'd guess that its the decorator...

Either way the command :

```
compiz --replace
```

run from the run command dialog (alt f2) ought to sort you out...you might need root access, I can't remember, if so prepend sudo to the command.

if that doesn't help then Id install the compiz icon which gives you a systray icon to relaunch the manager and the decorator nice and easily.

Hope that helps

---

### Post by clipse on 2008-09-23
> **vishzilla said:**
> try this command

```
metacity --replace
```

okay that worked. 

Thanks alot guys. :D

I'm a happy camper now. :)

---

### Post by G-Dub on 2008-09-23
Thats what i meant- X window manager.

---

### Post by clipse on 2008-09-23
Okay, I spoke too soon.  

When I type

metacity --replace

then I get the bar back but I loose the embedded terminal and AWN.

When I type 

compiz --replace

I get my embedded terminal back and AWN but I loose the window bar.


any ideas?

---

### Post by issih on 2008-09-23
Like I said your window decorator has crashed....

try doing:

```
sudo apt-get install fusion-icon
```

then launch the icon (I think it lives in Applications>System Tools>Compiz Fusion Icon)

Then click on the icon in the system tray and select the window decorator, if you have more than one option you could try toggling from one to the other and back again :)

Hope that helps

---

