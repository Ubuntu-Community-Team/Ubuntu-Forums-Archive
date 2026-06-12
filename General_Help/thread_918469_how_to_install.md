---
title: "how to install?"
date: 2008-09-12
forum: General Help
---

### Post by scuba_suit on 2008-09-12
i dl'ed the latest adobe flash player and it came as a tar.gz file. i clicked it and it has two files. one is the 'flashplayer-installer' file and the other is the 'libflashplayer.so', where do i put these files?

---

### Post by mb_webguy on 2008-09-13
The best way to install Flash 10 is to use the backports repository.  Check the link in my signature for details.

---

### Post by Tag_yer_dead on 2008-09-13
or you can type in terminal
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by mb_webguy on 2008-09-13
That doesn't install the newest version of Flash unless you have the backports repository enabled.

---

### Post by scuba_suit on 2008-09-13
nope, that sudo command doesn't work, i'm runnin gutsy, i tried running my update manager to find the latest flash update, nothing, i also have firefox 3, but i made a link to it on my desktop that always ask me if i want to run it from the terminal or 'run', i click 'run' to use it, but how do i do it so that when i click the ff icon (because it's ff2) it'll run ff3? how do i upgrade ff2? do i put the necessary files somewhere where the ff2 files are? i'm too used to windows and installing programs there...

by the way, i forgot to get the sudo kill command (when ff2 freezes up i have to use sudo kill) to terminate programs, i remember it being p-something...

---

### Post by scragar on 2008-09-13
if firefox dies run either of these 2:
```
killall firefox-bin
pkill firefox-bin
```

---

### Post by scuba_suit on 2008-09-16
i'm still trying to update flash, i run into this problem when i enter the: 

sudo apt-get install flashplugin-nonfree

i get:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem

what? how do i manually run it? and what seems to be the problem?

---

### Post by scragar on 2008-09-16
your last update must have been interupted, run the command it mentions like so:
```

sudo dpkg --configure -a

```
and wait for it to finish up.

---

### Post by scuba_suit on 2008-09-16
thanks scragar, hey do you know how to install wine?

---

### Post by scuba_suit on 2008-09-16
AND how do i update ff2 to ff3?

---

### Post by scragar on 2008-09-16
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update

sudo apt-get install wine
```

This will add wine to the repo's then install it(so you get all the updates installed automaticly). (it's not as complex as it sounds, the first line confirms that the wine repo is trusted, the second line updates the list, the third line updates the list of programs available from there repo's, and the final line downloads it)

---

### Post by scragar on 2008-09-16
> **scuba_suit said:**
> AND how do i update ff2 to ff3?

are you using gutsy(7.10) or hardy(8.04)

GUTSY way:
```

sudo apt-get remove firefox
sudo apt-get install firefox-3.0

```
HARDY way:
```

sudo apt-get remove firefox-2
sudo apt-get install firefox

```

---

