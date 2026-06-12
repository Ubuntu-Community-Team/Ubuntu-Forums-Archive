---
title: "Don't Start Gnome on Startup?"
date: 2008-09-09
forum: General Help
---

### Post by comspy on 2008-09-09
Hello There,

I am trying to make my Ubuntu 7.10 Desktop(8.04 wasn't working on my old system) installation *not* start Gnome on startup. I'm running this PC as a LAN LAMP server and want to only start Gnome when I need it. Is there a way to do this?

Thanks
Comspy

---

### Post by tuxulin on 2008-09-09
look here [http://ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html](http://ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html)

my guess is that you need to install sysv-rc-conf
sudo apt-get install sysv-rc-conf
then type
sudo sysv-rc-conf
then scroll down till you see gdm my guess is that you untick them


wether it works in ibex is something im not sure about 
good luck
tuxulin

---

### Post by Vivaldi Gloria on 2008-09-10
It has been a while I last did this. This is how I remeber to stop gdm from starting: restart your computer and press ESC to see grub boot menu. Choose recovery to boot to a recovery console. Give the command

```
update-rc.d gdm remove
```

or

```
update-rc.d -f gdm remove
```

and restart using the command

```
reboot
```

Now gnome won't start. You can start gnome with one of

```
startx
sudo /etc/init.d/gdm start

```

when you want.

I suggest you read the folowing to learn more about how ubuntu handles services:

[http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/](http://pthree.org/2008/02/26/managing-services-in-ubuntu-part-i-an-introduction-to-runlevels/)
[http://pthree.org/2008/02/27/managing-services-in-ubuntu-part-ii-managing-runlevels/](http://pthree.org/2008/02/27/managing-services-in-ubuntu-part-ii-managing-runlevels/)

---

### Post by matey3 on 2008-09-11
Thanks a lot everyone!


Cool link thanks:
> **tuxulin said:**
> look here [http://ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html](http://ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html)

my guess is that you need to install sysv-rc-conf
sudo apt-get install sysv-rc-conf
then type
sudo sysv-rc-conf
then scroll down till you see gdm my guess is that you untick them


wether it works in ibex is something im not sure about 
good luck
tuxulin


Thank You Vivaldi for the info...
oh...(being lazy)..

I just did a mini script like this(in case some run kdm or xdm as default);

update-rc.d -f gdm remove
update-rc.d -f kdm remove
update-rc.d -f xdm remove

And saved it as stop-x.sh then chmod 755 stop-x.sh
then I can run it. ./
You can also put the start in another script and call it start-x (or use CAPs/mix-n-match to make sure no conflict with other system file names)..

---

### Post by iam13013 on 2009-02-23
I needed to boot without gnome to install my nVidia Driver, so I used

> update-rc.d -f gdm remove

I had a bad feeling when I first did it, and my suspicions were correct, I can't figure out how to make Gnome startup at boot.

So how exactly do I fix this?

Thanks in Advance

---

### Post by zika on 2009-02-23
try first with```
sudo update-rc.d gdm install
```

---

### Post by makisupa123 on 2009-02-23
Read ```
man update-rc.d
```

pro tip:
```
sudo update-rc.d gdm defaults
```

should do the trick.

--Mak

---

