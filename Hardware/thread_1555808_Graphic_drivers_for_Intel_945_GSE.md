---
title: "Graphic drivers for Intel 945 GSE"
date: 2010-08-18
forum: Hardware
---

### Post by xaber1488 on 2010-08-18
Hi guys!

I just bought a packard bell dot s2 134 and everything works great with netbook remix 10.04.

The only thing I can't install are the graphic drivers for the Intel 945 GSE graphic card.

With lspci I get this:

VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller

The hardware installation lists no drivers available: what can I do?

Thanks in advance!

---

### Post by Fafler on 2010-08-18
They are already present. They are just rally slow. Such things are included within the Ubuntu installation. Sorry :-)

---

### Post by xaber1488 on 2010-08-18
Mmmmmm... So why can't I activate the effects in the gnome appearance config?

I didn't specify that I am trying the netbook via ubuntu live: I did not install the distro yet: are the drivers present in this way too?

---

### Post by Fafler on 2010-08-18
Thats actually kinda weird. Try opening a terminal and type

```
glxinfo | grep vendor
```

You should get something like

```
fafler@oxygen:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: DRI R300 Project
fafler@oxygen:~$ 
 
```

If it says software instead or disabled or something (can't really remember) instead of either SGI or Intel (dunno either) theres something wrong with your setup. You might want to read a guide on how to make effects work with the your chip.

[http://www.google.com/search?hl=en&q=N10+ubuntu+compiz](http://www.google.com/search?hl=en&q=N10+ubuntu+compiz)

---

### Post by ajgreeny on 2010-08-18
The default UNE version does not include compiz, needed for desktop effects, that's why you can't enable them.  You can install compiz and all its dependencies easily enough if you want to.

---

### Post by kerry_s on 2010-08-18
just to let you know compiz & netbook do not play nice together, sure thats why it's not included.

if you need composting for a dock, you can use metacity or xcompmgr, you'll have to turn off undecorate for maximus or your panel will go invisible.

---

### Post by xaber1488 on 2010-08-19
Thank you guys! I simply installed compiz! Anyway, if I experience problems, I'll sure switch to xcompmgr: I'm having a great experience with it under crunchbang linux statler!

Thank you!

---

### Post by xaber1488 on 2010-08-19
Btw, how to add solved?

---

### Post by ajgreeny on 2010-08-19
As the OP, you can go to the top of the thread and click on "Thread Tools" and there you will find "Mark as solved".

---

