---
title: "Menu list in KDE4"
date: 2008-07-28
forum: General Help
---

### Post by schreckles on 2008-07-28
I just switched my laptop over from ubuntu 8.04.1 to kubuntu 8.04.1 KDE4 Remix last night and I was simply wondering where the menu list is. In ubuntu, it's just under the system tab, then you can go in there and add stuff to your applications list. Anyone know how to add or remove stuff from the applications lists in the K Menu?

---

### Post by caljohnsmith on 2008-07-28
If you right-click on the Kmenu, does it give you an option for "menu editor"?

---

### Post by schreckles on 2008-07-28
> **caljohnsmith said:**
> If you right-click on the Kmenu, does it give you an option for "menu editor"?

Nope....I have "Application launcher settings" and "Panel settings" aside from remove options

---

### Post by caljohnsmith on 2008-07-28
OK, can you run it from the command line, i.e. "kmenuedit"?

---

### Post by schreckles on 2008-07-28
Hmmm..didn't realize that was a command lol...guess I'll try that here in a sec...thanks

---

### Post by schreckles on 2008-07-28
...apparently it isn't a command

---

### Post by kuja on 2008-07-28
I'm guessing it might not exist in 4.0. It does however exist in KDE 4.1. You can install the RC with this repo: ```
deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu hardy main
``` Just add that to your /etc/apt/sources.list and do a ```
 sudo apt-get update && sudo apt-get upgrade
``` Or you could just wait for the actual release and grab it from backports then, which won't be long from now. It'll be well worth the upgrade, kde 4.1 is a large step from 4.0.

---

