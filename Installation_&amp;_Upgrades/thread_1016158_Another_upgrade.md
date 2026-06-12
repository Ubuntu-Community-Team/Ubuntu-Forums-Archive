---
title: "Another upgrade?"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by winol5 on 2008-12-19
Hey! today an uprage manager poped in my task bar I just clicked it and it sayscomething about a partial update of the packages, when I choose to make the partial upgrade the window that appears when uodating from version to version popups, I have ubunu 8.10 so I dont know why this appears today.

It says it will unistall 1 package, install 3 brand new ones and upgrade 19 more.

The details says that it will install the linux headers,unistall linux-generic, and uograde plugins and libs like libavahi, and the flash plugin

---

### Post by oilchangeguy on 2008-12-19
> **winol5 said:**
> Hey! today an uprage manager poped in my task bar I just clicked it and it sayscomething about a partial update of the packages, when I choose to make the partial upgrade the window that appears when uodating from version to version popups, I have ubunu 8.10 so I dont know why this appears today.

It says it will unistall 1 package, install 3 brand new ones and upgrade 19 more.

The details says that it will install the linux headers,unistall linux-generic, and uograde plugins and libs like libavahi, and the flash plugin

just do it. new updates are released many times over the life of an operating system.

---

### Post by taurus on 2008-12-19
Close the update-manager.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by winol5 on 2008-12-19
Yeah I know, but it seems to me just very strange that the manager of "complete distribution upgrade" appears in the middle of 8.10 o.0

---

### Post by cariboo on 2008-12-19
IF update-manager wants to do a partial upgrade, I would run in a termianl:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

Stay away from partial upgrades, as you could end up with a system that doesn't work the way you expect it to.

Jim

---

### Post by oilchangeguy on 2008-12-19
> **winol5 said:**
> Yeah I know, but it seems to me just very strange that the manager of "complete distribution upgrade" appears in the middle of 8.10 o.0

ok, you seem to be using the words upgrade, and update like they mean the same thing. they don't, yes do all updates to 8.10. if you're being prompted to upgrade to 9.04, don't do it. it's still in alpha.

---

### Post by winol5 on 2008-12-19
[IMG]http://xs434.xs.to/xs434/08515/1239.png[/IMG]
[IMG]http://xs434.xs.to/xs434/08515/2124.png[/IMG]

---

### Post by pastalavista on 2008-12-19
most of us have seen all that before... what was your question?

try system>applications>'cruft remover' or 'remove orphaned packages' and if it still happens, open 'synaptic package manager' and search for broken packages

(if you use cruft remover, be careful not to remove anything you installed and want to keep. it only recognizes Ubuntu 'approved' software)

---

### Post by winol5 on 2008-12-19
theres no orphaned packages, how do I search for broken ones in synaptic? I open the manager and then  on custom filters I click broken and there's nothing

---

### Post by winol5 on 2008-12-19
*bump*

---

### Post by wwusnobrdr on 2008-12-20
I did the partial upgrade to the latest kernel and it has broken a few things as far as I can tell.  I rebuilt my Virtualbox kernel driver but now when I load VM's there is no keyboard and when the system shuts down I see a tty error.  The wireless was broken, but fixed that getting the latest compat-wireless package.  Seems to be other random problems popping up so I am hoping for some new updates soon.  Might want to wait on this one...

---

### Post by cb34 on 2008-12-20
i have the EXACT same problem.. exactly.

i went through with the partial update, said the exact same thing as you, now just like you, i have 1 package that wont upgrade, says the same thing.

this is not normal.. there is some problem. this last update was not normal at all.
so far no problems except i was playin with simple-ccsm and it locked my whole machine when i tried to change some major setting. maybe it's from this update problem, or maybe not.. i now have 1 package sitting that cant be installed, and i just hope things aren't totally damaged now.

i'm having enough problems with intrepid crashing to the login screen..

anywayz...

same exact problem here. what's goin on? something's wrong with this. i'm sure of it.

EDIT-> oops, i'm rude..hehe.. i meant to say..

can someone please help me and wwusnobrdr with this issue.
i have a feeling some crashes might come from this.. maybe.. i hope not. :D

---

### Post by zika on 2008-12-20
whenever in doubt or being offered partial upgrade go to Synaptic and Reload, Mark and Apply.

---

### Post by blakjesus on 2008-12-20
I am experiencing this problem too. Why is it asking me to do a partial upgrade in Ubuntu? This is the first time i have run into this issue.

> **zika said:**
> whenever in doubt or being offered partial upgrade go to Synaptic and Reload, Mark and Apply.

I did that and when it finished it gave me an error saying something about a GPG error and that Ubuntu Archive Automatic Signing Key is invalid. Whats going on?

---

### Post by ugm6hr on 2008-12-20
Have you added any non-official packages (e.g. OO.org 3.0etc)?

Have you added any non-official repos?

If yes: then there is a conflict between these and the latest Ibex updates.

Consider removing them, and then reinstalling ubuntu-desktop:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by blakjesus on 2008-12-20
I did add a repository for Open Office 3, so i tried what you said. After reinstalling ubuntu-desktop through synaptic, i tried to run update manager and i returned with this message:

> GPG error: [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.bz2)  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ugm6hr on 2008-12-20
In Software Sources, try selecting a different server (e.g. Main Server).

Then try again.

---

### Post by blakjesus on 2008-12-20
Tried a different server. Still no good.

---

### Post by zika on 2008-12-20
> **blakjesus said:**
> I am experiencing this problem too. Why is it asking me to do a partial upgrade in Ubuntu? This is the first time i have run into this issue.

I did that and when it finished it gave me an error saying something about a GPG error and that Ubuntu Archive Automatic Signing Key is invalid. Whats going on?

did it give You an option to accept it eventhough UAASKey is invalid? if it did, accept it, it's not a big deal, just a way to prevent of making Ubuntu responsible. I did ...

---

### Post by blakjesus on 2008-12-20
No, it just gives me an option to close the window and it still asks me to perform a partial upgrade.

---

### Post by cb34 on 2008-12-20
wierd... after doing the same thing a bunch of times..IT NOW WORKED.. IT UPDATED! along with 2 other updtes.. woohoo! im happy.. hehe

i went into UPDATE MANAGER(which i previously did many times over), did CHECK, and the non-selectable package is now selected along with 2 other packages.

it worked.. updated like normal..

try it again everyone.. maybe they just updated something. :D

---

### Post by Ivo Moelans on 2008-12-20
I can confirm what cb34 wrote. Apparently they 'updated the update'. Three restricted module files were installed like normal.
I had to change my server to the Main Server in *System&#8594;Administration&#8594;Software Sources* though. My local server hadn't received the new restricted modules yet.

So, this thread can be marked 'Solved'.

---

