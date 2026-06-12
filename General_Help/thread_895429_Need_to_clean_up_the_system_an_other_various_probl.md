---
title: "Need to clean up the system an other various problem of Hardy Heron installation."
date: 2008-08-20
forum: General Help
---

### Post by porlaizquierda on 2008-08-20
The installation process froze and it seems that most of the stuff is installed, except for the red X where the icon for Firefox should be. Is there anything I can do that will install whatever might be lacking with the Hardy heron upgrade and then clean up my system before restarting my computer?

Plus, when I do start up my computer I get a popup icon thet says:  Internal error failed to initialize HAL!

Someone please help.

---

### Post by arist0tle on 2008-08-20
hmmmm. I would google that HAL error. HAL is your hardware abstraction layer. very important. although if you started in X and mostly everything is working you are pbly ok. I'm not sure if there is a way to install anything that wasnt installed. Maybe some apt-get trickery. anyone know?

---

### Post by ellgor on 2008-08-20
Hi,

You can try this, (if you can login as normal open a terminal) if not at the boot-up screen choose safe-mode and eventually you will be at the command line anyway, whichever way, type in:

sudo dpkg --configure -a

(if its a root command line you will not need the sudo)

if this produces no response then type this in:

sudo apt-get -f install

Any packages will be loaded, hopefully, if any errors occur alternate the two commands until the process is finished, once it has you should be able to reboot normally. hope this is of help.
 
Regards, Ellgor.

---

### Post by porlaizquierda on 2008-08-23
Ok. It's doing stuff, but it stays at Generating locales. Is that doing anything? Should I wait until something happens?

---

### Post by porlaizquierda on 2008-08-23
I should also mention that the internet does not work on my computer since I've had this problem. I know it's not my connection since my computer is doing the same thing at a friend's house who has a perfectly fine connection.

---

