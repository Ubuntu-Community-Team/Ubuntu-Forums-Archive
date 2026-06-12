---
title: "how to boot in text mode"
date: 2008-08-06
forum: General Help
---

### Post by camelgrass on 2008-08-06
Hello, from the GRUB menu I can select Ubuntu 8.04 but how do I boot in text mode?

Thank you!
Marty

---

### Post by justleen on 2008-08-06
have a look at this thread, specificaly the final post
[http://www.linuxquestions.org/questions/ubuntu-63/since-we-have-no-etcinittab-506281/](http://www.linuxquestions.org/questions/ubuntu-63/since-we-have-no-etcinittab-506281/)

---

### Post by pro003 on 2008-08-06
You'll boot in text mode if you mean install ubuntu in text mode when you get ubuntu alternate install cd... if you meant that you already have install ubuntu you'll probably have to select repair / recovery mode and there you go...

hope i helped some...

---

### Post by spiderbatdad on 2008-08-06
do you want to do this persistently or occasionally?

selecting single or recovery will boot you one time into text mode, or you could do something like edit /etc/rc2d/S30gdm, by changing the S to a t (for example) would prevent the script from being called...there.

Or sudo apt-get install rcconf then run rcconf with sudo rcconf you can control runlevel tools here like gdm. use <tab> and <arrows> to navigate to <ok> <cancel>

---

### Post by angry_johnnie on 2008-08-06
To go into text mode from a normal x session:

press Ctrl + Alt + F1

That will drop you to a virtual terminal.

To get back to GUI, press Ctrl + Alt + F7

If you want to kill the GUI from a virtual terminal, type:

```
sudo /etc/init.d/gdm stop
```

Then, to get back to GUI, type:

```
sudo /etc/init.d/gdm start
```

If you want to make it permanent, so you'll always boot into text mode, go to **System > Administration > Services > Unlock** and disable GDM.

To get back to X, type either

```
startx
```

or 

```
sudo /etc/init.d/gdm start
```

After that, if you want to enable booting into an xsession again, you'll have to go to **System > Administration > Services > Unlock** and enable GDM.

---

