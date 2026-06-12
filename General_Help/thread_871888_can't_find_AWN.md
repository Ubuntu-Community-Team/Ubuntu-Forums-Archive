---
title: "can't find AWN"
date: 2008-07-27
forum: General Help
---

### Post by RajaAjmal on 2008-07-27
i've installed AWN form synaptic and it was OK. then i've added the below lines in the sources.list 

[B]#FILE: /etc/apt/sources.list
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main[/B]

plus i've write the below cammand in the terminal

[B]$ sudo apt-get update
$ sudo apt-get install awn-core-applets-bzr
[/B]
after  typing the command, i can see some processing in the terminal.
And now i can no more find AWN in the application and neither in system->preferences.

help please

---

### Post by RajaAjmal on 2008-07-27
i've installed AWN form synaptic and it was OK. then i've added the below lines in the sources.list 

[B]#FILE: /etc/apt/sources.list
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main[/B]

plus i've write the below cammand in the terminal

[B]$ sudo apt-get update
$ sudo apt-get install awn-core-applets-bzr
[/B]
after  typing the command, i can see some processing in the terminal.
And now i can no more find AWN in the application and neither in system->preferences.

help please

---

### Post by thewolf32 on 2008-07-27
Tells us if you can run it doing this:

Press Alt-F2, and in the box write: avant-window-navigator

And press "Run".

Tells us if it runs by doing that.

---

### Post by stevoo on 2008-07-27
well awn should be automitically in the repos. 
Unless you removed something essential from your sources.list then it should be ok

Try the Synaptic package manager 
and search for : awn

---

### Post by RajaAjmal on 2008-07-27
thanks to come to my help thewolf but it does not run. i got this error message.
Could not open location 'file:///home/raja/avant-window-navigator'

---

### Post by thewolf32 on 2008-07-27
Are you using Gutsy or Hardy?

---

### Post by RajaAjmal on 2008-07-27
thanks to come for help stevoo, but then what next?
when type awn in synaptic i can see that awn-core-applets-bzr is marked as installed, but awn-manager and awn-manager-bzr is unmarked.
please give step by step instructions. i'm new to ubuntu.

---

### Post by RajaAjmal on 2008-07-27
i think Hardy. how to know?

---

### Post by thewolf32 on 2008-07-27
System > About Ubuntu.

It should say there.

---

### Post by RajaAjmal on 2008-07-27
all i know its ubuntu 8.04

---

### Post by stevoo on 2008-07-27
you need awn-manager-bzr installed so tick that one and istall it

after that check in Applications -> accesories

You will find a new Icon Avant Windows Navigator 
Click on  that and the awn will open on the bottom.

You can go into the properties if you right click on the AWN canvas and select preferences.

Post for follow ups

---

### Post by RajaAjmal on 2008-07-27
yes it's hardy

---

### Post by northern lights on 2008-07-27
AWN can even be installed from the "Add/Remove" menu:

Applications > Add/Remove... > select 'Show: All available applications' > search for 'Avant' > check the box next to AWN > Apply Changes > Close

---

### Post by Joeb454 on 2008-07-27
Threads merged.

Please do not create duplicate threads on the same issue

---

### Post by thewolf32 on 2008-07-27
If you have hardy, then probably this is the problem.

You added the repository for gusty, not for hardy (8.04).

You added:
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) **gutsy** main

It should be:
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) **hardy** main

Replace the repository, and reinstall AWN.

---

### Post by gjoellee on 2008-07-27
you can install AWN easily from this graphical install software....download it here: [http://linux.softpedia.com/get/System/Installer-Setup/Ultamatix-39892.shtml](http://linux.softpedia.com/get/System/Installer-Setup/Ultamatix-39892.shtml)

---

### Post by northern lights on 2008-07-27
> **thewolf32 said:**
> Replace the repository, and reinstall AWN.
Just undo all the changes you've sofar made to your 'sources.list' and bring it back to where it was before.

> **gjoellee said:**
> you can install AWN easily from this graphical install software....download it here: [http://linux.softpedia.com/get/System/Installer-Setup/Ultamatix-39892.shtml](http://linux.softpedia.com/get/System/Installer-Setup/Ultamatix-39892.shtml)
AWN is not only in the repos, it's listed in the 'Add/Remove...' dialog. Give me one good reason for why you'd need another installer???
:-k

Compare:> **northern lights said:**
> AWN can even be installed from the "Add/Remove" menu:

Applications > Add/Remove... > select 'Show: All available applications' > search for 'Avant' > check the box next to AWN > Apply Changes > Close

Can you say "simple"?

---

### Post by RajaAjmal on 2008-07-27
how to replace the repository? plus i can't install awn neither from synaptic nor from add/remove application. when try to add avant from add/remove application, i got the following error msg
[B]Cannot install 'avant-window-navigator'

This application conflicts with other installed software. To install 'avant-window-navigator' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/B]
i've also remove 
awn-core-applets-bzr 
from synaptic. still i get the error msg form add/remove app

---

### Post by northern lights on 2008-07-27
Post your 'sources.list'. Run ```
gedit /etc/apt/sources.list
```, copy all the text and, in a new post, paste it into codetags (pound symbol).

I'll tell you what to remove.

Further, run ```
sudo apt-get autoremove avant-window-navigator awn-manager libawn-dev libawn0 python-awn awn-core-applets-bzr
```

And maybe also ```
sudo aptitude purge avant-window-navigator
```

Wait till the repos are removed. Run an update after removal. Then reinstall.

---

### Post by RajaAjmal on 2008-07-28
northern lights thanks for your help. in fact i've managed to get the awn back. iv'e just restore my system form backup i've made, and everything has return as before.
thanks again.

---

