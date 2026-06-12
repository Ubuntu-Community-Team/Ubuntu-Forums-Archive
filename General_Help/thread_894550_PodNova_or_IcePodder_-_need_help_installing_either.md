---
title: "PodNova or IcePodder - need help installing either"
date: 2008-08-19
forum: General Help
---

### Post by zami on 2008-08-19
I am totally stumped on installing either of these programs.

PodNova  2.4
all instructions online I've found involve using a file named
install.sh
there is no such file in version 2.4 (the current version as of this writing) so am I absolutely clueless about what to do with this heap of python files.

IcePodder 5.4
this version (current as of this writing) requires the package
python-xmms
not available via synaptic
there is a "python-xmmsclient" package installed, but the icepodder .deb still complains that I don't have "python-xmms"

Any help for installing either of these programs?

Thanks!

-zami

---

### Post by indiv on 2008-08-19
Well, it didn't work on my system for some reason.  But the setup file is called setup.pyc.  I'm assuming you're supposed to just run that, but it failed for me, and I don't know enough about python to figure it out.

First you may need to install setuptools and I had to install plistlib:
sudo apt-get install python-setuptools
sudo apt-get install python-plistlib

tar xzvf PodNova-2.4-linux-py25.tar.gz
cd PodNova-2.4-linux-py25
python setup.pyc

Once it failed, I had to delete the directory PodNova-2.4-linux-py25 and then start over because 'python setup.pyc' didn't work like it did when I first tried to install.  It didn't fail because of a missing dependency, though, so I couldn't figure it out.

Here are some other dependencies I installed to be able to run the client directly without running setup first (*python PodNova.pyc*):
sudo apt-get install python-wxtools
sudo apt-get install python-egenix-mxdatetime

Anyway, maybe this info will work for you, or get you closer at least.

---

### Post by samjetski on 2009-07-05
Hey guys,

> IcePodder 5.4
this version (current as of this writing) requires the package
python-xmms
not available via synaptic
there is a "python-xmmsclient" package installed, but the icepodder .deb still complains that I don't have "python-xmms"

Yea, when I tried to install python-xmms using apt-get (the command-line equivalent of synaptic) it said that the package didn't exist, but that another package refered to it. I did a web search, and apparently the python-xmms package is no longer being maintained, but it's not needed anyway.

There's a modified version of the IcePodder package available that doesn't depend on python-xmms. I managed to install it and it worked fine. See here: [http://www.icepodder.com/forum/viewtopic.php?t=43&sid=a84cc9b9464418f2fe363cf3e55029b7]("http://www.icepodder.com/forum/viewtopic.php?t=43&sid=a84cc9b9464418f2fe363cf3e55029b7")

> PodNova 2.4
all instructions online I've found involve using a file named
install.sh
there is no such file in version 2.4 (the current version as of this writing) so am I absolutely clueless about what to do with this heap of python files.

Yea, I've found some various stuff about PodNova. They seem to have removed that script in the recent versions. Unfortunately the step by step instructions mentioned in [this thread]("http://ubuntuforums.org/showthread.php?t=324752") appears to have been removed or broken.

> Here are some other dependencies I installed to be able to run the client directly without running setup first (python PodNova.pyc): ...

Some of the questions on forums refer to moving the entire program folder into /opt or /usr or a similar directory ([as in this thread]("http://www.linuxforums.org/forum/ubuntu-help/93828-podnova-start.html")), as though that is a standard procedure with this sort of thing. Maybe that's the way to go?

---

### Post by samjetski on 2009-07-05
Got it working and I'm loving it!

Here's how I did it:
```
sudo tar --directory /opt -xzvf PodNova-2.4-linux-py25.tar.gz
sudo mv /opt/PodNova-2.4-linux-py25/ /opt/podnova/
```

To run:
```
cd /opt/podnova
python PodNova.pyc
```

Note that ```
python /opt/podnova/PodNova.pyc
``` does not work.

To be able to make a menu item or shortcut for it (or to run it easily from the terminal) I had to make a small script to run it:
```
#!/bin/bash
# Little script to run podnova
echo Starting PodNova...
cd /opt/podnova/
python PodNova.pyc
```

I named this file "podnova". Then I made it executable and copied it to a binaries folder:

```
sudo chmod 755 podnova
sudo cp podnova /usr/bin/
```

Then when you make a menu item or shortcut you simply type "podnova" (without quotes) in the command box. To modify/add to your main menu items, run:
```
alacarte
```

When I created a shortcut/menu item I used this file as the icon:
/opt/podnova/resources/podnova.ico

Hope this helps some people.
Cheers :D

PS: I did all of this on Ubuntu 8.10 Intrepid

---

