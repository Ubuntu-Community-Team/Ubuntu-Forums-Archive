---
title: "[SOLVED] No protocol specified cannot open display:"
date: 2008-07-13
forum: General Help
---

### Post by morbid_bean on 2008-07-13
Im just simply wanting to install some drivers for my radeon 9200 using this guide   " [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) "   but when i get the the part where i need to edit xorg.conf file ill get this


```
 sudo gedit /etc/X11/xorg.conf
No protocol specified
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

```

so i say well great then ill just go ahead and edit the graphical way by navigating through natulius....

```
 sudo nautilus
No protocol specified
cannot open display: 
Run 'nautilus --help' to see a full list of available command line options.

```


The hecks going on!?:confused:

---

### Post by dracayr on 2008-07-13
did you do that from a tty?
you can also edit files using nano or vim:

sudo vim /etc/X11/xorg.conf

dracayr

---

### Post by morbid_bean on 2008-07-13
Fixed it....simple restart of my machine :oops:

---

### Post by mcgiwer on 2010-10-19
I have same problems on my Ubuntu, but restarting of the machine don't help

---

### Post by cmcginty on 2011-01-08
Check the ownership of **~/.ICEAuthority** file. It must be writable. I was seeing these error on the command line when X would not start.

---

### Post by hawstom on 2012-02-29
My issue happened after an update forced a restart.  Restarting again resolved the issue for me.

---

### Post by oldos2er on 2012-02-29
Closed, necromancy.

---

