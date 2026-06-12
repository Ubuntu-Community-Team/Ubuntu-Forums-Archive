---
title: "Where to install????"
date: 2009-07-07
forum: Installation &amp; Upgrades
---

### Post by renbla on 2009-07-07
I want to install pygobject and pygtk, in tha readme file it said --prefix=<prefix where python is installed>, so should i install them in /usr/local/bin or /usr/local/lib/python2.xx ?????

And i'm sure i installed pygobject(2.18 ) succesfuly but when i try to configure pygtk(2.15) it said :"
checking for PYGOBJECT... configure: error: Package requirements (pygobject-2.0 >= 2.16.1) were not met:

No package 'pygobject-2.0' found"
 
Can smb help me please !!!!!!!!!!!!:(:(:(

---

### Post by dstew on 2009-07-07
What flavor of Ubuntu do you have? How are you trying to install this software? I see a package in Synaptic for pygtk, called python-zebrapygtk. Did you try to install it using Synaptic?

---

### Post by washakie on 2009-07-07
Note: this applies to python2.6

Use the packages if available, it will save you a lot of headaches!

However, if you do custom install some packages, here's a point I recently learned.

aptitude/synaptic/apt will put the distribution python packages here:
/usr/lib/python2.6/dist-packages

However, if you do a custom install, simply put them in:
/usr/local/lib/python2.6/dist-package

Then, in your .bashrc file (assuming you're using bash), make sure you have the PYTHONPATH variable set:

PYTHONPATH=${PYTHONPATH}:.:~/bin:/usr/local/lib/python2.6/dist-packages
export PYTHONPATH

Then your python will look there first, before pulling in the packages from the distribution. I learned this for numpy. 

Good luck.

---

### Post by renbla on 2009-07-08
Sorry for not replying, been busy at school ~.~
@dstew: srr but i can't find any package name python-zebrapygtk. actually, before trying to compile from source, i have messed around w/ synaptic for a long time and i screwed up, now every time i want to do smt w/ synaptic, it said that it has to remove some package :"alacarte deskbar-applet deskbar-applet-dbg fast-user-switch-applet gedit
  gnome gnome-applets gnome-control-center gnome-core
  gnome-desktop-environment gnome-menus gnome-office gnome-panel
  gnome-terminal libsqlite3-dev nautilus nautilus-cd-burner python-all-dev
  python-dev python-glade2 python-glade2-dbg python-gnome2-dbg
  python-gnome2-desktop-dbg python-gnome2-extras-dbg python-gobject-dbg
  python-gobject-dev python-gtk2-dbg python-gtk2-dev python-gtkhtml2-dbg
  python-gtkmvc python2.5-dev serpentine startupmanager
0 upgraded, 0 newly installed, 33 to remove and 281 not upgraded.
After this operation, 68.7MB disk space will be freed."
I think it's trying to remove gnome ????? can you tell me why and how can i fix this???[U]
@washakie :[/U]i did exactly what you said, i use --prefix=/usr/local/lib/python2.6/dist-pakage to pygobject <~~ no problem, and then when i use --prefix=/usr/local/lib/python2.6/dist-pakage to configure pygtk<~~~~~ still the same error, can't find pygobject :(

Please help me!! :( any help is appreciated.

---

### Post by renbla on 2009-07-08
> **dstew said:**
> What flavor of Ubuntu do you have? 
<~~~~~ what do you mean????? I am using ubuntu 8.04 hardy if you want to know :)

---

### Post by renbla on 2009-07-08
Something is really funny: if i use --prefix=/usr for pygobject and pygtk then it's ok, noproblem to insall but when i  type import pygtk in python it returned no module name pygtk????? if i use --prefix=/usr/local for pygobject and pygtk ~~~~~~~~> can't find pygobject....... :( . I'm considering installing python in /usr instead of /usr/local...

---

### Post by dstew on 2009-07-08
> i can't find any package name python-zebrapygtkIt is [here]("http://packages.ubuntu.com/search?keywords=pygtk&searchon=names&suite=jaunty&section=all"). You need to activate the Universe repository. See [this How-To]("https://help.ubuntu.com/community/Repositories/Ubuntu").

EDIT: Sorry, that is the Jaunty package, you are using Hardy, so you are right, the package does not exist for Hardy 8.04. I don't have any more ideas for you right now.

---

### Post by renbla on 2009-07-08
ok i get python pygobject and pygtk work fine when i use --prefix=/usr for all of them and i can also import gtk without any problem. But i still have no idea why i can't use --prefix=/usr/local ??. But i think i should forget a bout that..... too much thinking..... >.<(that's the problem for a newbie like me, thinking a lot but don't know what to think =.=")

---

