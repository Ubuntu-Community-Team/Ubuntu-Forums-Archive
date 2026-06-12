---
title: "simple way to install dockbarx?"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by goosemontana on 2009-09-07
ive read a few guides and tried a few times to install dockbarx, but its never worked, or i didnt know how to do the next step. im new to ubuntu and i was wondering if someone could post a simple  guide on how to install dockbarx. i allready switched my desktop to the default ubuntu desktop i just need help installing dockbarx

---

### Post by Partyboi2 on 2009-09-08
Open a terminal (Applications>Accessories>Terminal) and install some required packages with
```
sudo apt-get install python-gnome2-desktop python-numpy
```
then grab dockbarx with
```
wget http://www.gnome-look.org/CONTENT/content-files/101604-dockbarx_0.21.11.tar.gz
```
then extract it with
```
tar xvzf 101604-dockbarx_0.21.11.tar.gz
```
then enter the source directory
```
cd dockbarx_0.21.11
```
then copy dockbarx.py to /usr/bin and GNOME_DockBarXApplet.server to  /usr/lib/bonobo/servers
```
sudo cp dockbarx.py /usr/bin
sudo cp GNOME_DockBarXApplet.server /usr/lib/bonobo/servers

```
then create the themes directory with
```
sudo mkdir -p /usr/share/dockbar/themes
```
then cp the themes over with
```
sudo cp  themes/* /usr/share/dockbar/themes
``` then refresh the gnome panel by
```
killall gnome-panel
``` then right click on the top or bottom panel (Choose the panel where you want dockbarx) then choose "Add to Panel" and add "DockBar X Applet"

---

### Post by Felliph3 on 2009-12-05
I did this and it didnt work for me? I get a msg saying

The panel encountered a problem while loading "OAFIID:GNOME_DockBarXApplet".
Do you want to delete the configuration?

---

### Post by HomoGleek on 2009-12-13
> **Felliph3 said:**
> I did this and it didnt work for me? I get a msg saying

The panel encountered a problem while loading "OAFIID:GNOME_DockBarXApplet".
Do you want to delete the configuration?
I found a PPA for it

goto System > Administration > Software Sources > Other Software tab
Hit add, then you want too type ppa:dockbar-main/ppa

Then fire up the terminal and type
```

sudo apt-get install dockbarx

```

Then you just have too add it too the panel

---

### Post by Felliph3 on 2009-12-13
Thanks man, I found out what the problem was. I had gotten it from the PPA but the problem here was that when you enable  gnome-global-menu applet for GTK applications a few apps dont work. System monitor doesnt open when its enabled and same for the dock, I disabled it an dockbarX fires right up!

---

### Post by neeraj2608 on 2010-01-19
> **Felliph3 said:**
> I did this and it didnt work for me? I get a msg saying

The panel encountered a problem while loading "OAFIID:GNOME_DockBarXApplet".
Do you want to delete the configuration?

If you don't have gnome-global-menu and you're still having this problem, try reinstalling gnome-applets and gnome-applets-data. It worked for me.

---

### Post by neeraj2608 on 2010-01-19
> **neeraj2608 said:**
> If you don't have gnome-global-menu and you're still having this problem, try reinstalling gnome-applets and gnome-applets-data. It worked for me.

Sorry, scratch that. I rebooted my machine and the problem's still there. :(

---

### Post by krapp on 2010-03-25
> **Partyboi2 said:**
> Open a terminal 
then create the themes directory with
```
sudo mkdir -p /usr/share/dockbar/themes
```
then cp the themes over with
```
sudo cp  themes/* /usr/share/dockbar/themes
```

Shouldn't these lines read dockbarx rather than simply dockbar? Otherwise these directions worked for me for the latest (0.24.1) and on Ubuntu 9.10. Thanks!

---

### Post by elidoperezmd on 2010-06-05
> **Felliph3 said:**
> Thanks man, I found out what the problem was. I had gotten it from the PPA but the problem here was that when you enable  gnome-global-menu applet for GTK applications a few apps dont work. System monitor doesnt open when its enabled and same for the dock, I disabled it an dockbarX fires right up!

i know i has been quite a while sonce u worte this...but please, what do you mean?

thanks

---

