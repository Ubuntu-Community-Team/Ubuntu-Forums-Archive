---
title: "System profile"
date: 2008-11-01
forum: General Help
---

### Post by rmcellig on 2008-11-01
Is there any way I can get a profile of my computer (maybe a GUI solution) like the type of processor used, processor speed, memory config, video card used etc... 

I know I only have 512MB of RAM. Would more RAM increase the speed of Ubuntu? Right now it is kind of choppy. The PC I am using was made by me a few years ago. The reason I would like a system profile is so that I might be able to upgrade the RAM, processor etc...

---

### Post by beno1990 on 2008-11-01
```
sudo apt-get install lshw-gtk
```

You should be able to find that in your menus after install. Or you could just type its name (lshw-gtk) in the terminal again.

---

### Post by sdennie on 2008-11-01
You can also use:

```

sudo lshw

```

Or, probably better:

```

sudo lshw -html > hardware.html

```

That will create a file (hardware.html) that is easy to read via a web browser.

As for upgrading your RAM beyond 512M, yes, the machine will run faster with 1G or more or RAM.  512M is reasonable to run Ubuntu but, I wouldn't consider it optimal.

---

### Post by rmcellig on 2008-11-01
Is there a GUI app that will do this?

Thanks. Where is the hardware.html file saved?

---

### Post by tvtech on 2008-11-01
there is kind of a gui app go into Applications>Add/Remove

once there enable all software and type in device manager   it may not give you enough information though. you may want the lshw instead

---

### Post by beno1990 on 2008-11-02
> **rmcellig said:**
> Is there a GUI app that will do this?

Thanks. Where is the hardware.html file saved?

My first post above is the GUI version of lshw.:)

When you install it, you should be able to find it somewhere in your menus as "hardware lister".

---

