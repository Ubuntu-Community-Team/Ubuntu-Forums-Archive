---
title: "I want ksynaptic or synaptic"
date: 2005-11-18
forum: General Help
---

### Post by coolclassic on 2005-11-18
I have installed both kynaptic and synaptic using adept and although adept says there installed they are not. I have use locate and find from k menu to search for them, but they are not there. 

Before any one says use adept it is better, I will disagree. Adept does not finish installing packages I have to run dpkg --configure -a after every reboot and finding software in linux is bad enough because of criptic names but to trawel through 1000's of files in alphabetical order is a joke. Software should be in sub menus so you have some idea what they are for and the filtering system is a joke.

Sorry about the rant but I want synaptic/kynaptic

---

### Post by Kyral on 2005-11-18
If you want to be sure its installed, then try this

```
apt-cache policy synaptic
```

And you may want to try the Debian Menu

```
sudo apt-get install menu && update-menus
```

But then again I don't have much experiance with KDE so...

---

### Post by uberlinux on 2005-11-18
have you just tried running the command 'kdesu synaptic'?

---

### Post by coolclassic on 2005-11-18
kdesu just hangs in terminal.

---

### Post by aysiu on 2005-11-18
Don't put ```
kdesu
``` in a terminal by itself.
Open up a **Run command** dialogue and type in ```
kdesu synaptic
```

---

### Post by coolclassic on 2005-11-19
Sorry the full command entered was kdesu synaptic I also tried with other k packages i.e. kwrite, kate. and kdesu did not work.

By the way su does work.

---

