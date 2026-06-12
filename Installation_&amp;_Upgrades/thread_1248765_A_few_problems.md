---
title: "A few problems"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by m0ar on 2009-08-24
Hi there!

I have some trouble with my freshly installed ubntu/mint distro, kernel 2.6.28-11-generic.
I'm using an Acer Asprire 5738G notebook.

1; I can't get ANY audio out my 3,5mm-port. The cable to my reciever is plugged in, yet the sound comes out of the laptop speakers!  

2; I'm unable to update my kernel version by some wierd reason, i need to do that to apply a fix for the well-known ipv6-problem. What i get is;  Error: Dependency is not satisfiable: linux-headers-2.6.29-02062903     and that applies to ALL kernel versions i try to install.



I would really appreciate your help :3

---

### Post by starcraft.man on 2009-08-24
1. See the Volume control mixer. Go to preferences, add all relevant ones for playback and ensure that none are muted and all are loud. Go to System > Preferences > Sound On audio playback try several different soundsystems like pulse, alsa or any other listed until ya hear something. Audio is very fiddly when not enabled by default. Keep playing with both panels and inevitably it will work.

2. Odd. Can you paste here the output of the following command. Open a terminal (applications > Accessories > terminal) and type it in and return.
```
gksudo gedit /etc/apt/sources.list
```

Seems like its trying to fetch some unavailable package, did ya try installing that kernel? For the output of above command, please, put it in CODE tags (on the gui for text, # one) select all text then push button. Prevents page from dragging on forever. Want sources list, seems to be trying to fetch something not available.

Also, try following two commands and report back what they say.

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by m0ar on 2009-08-25
THAAAAAAAAAAAAAAAAAAAANKS for fixing my sound :3

The "Front" channel was my laptop speakers, and the "surround" was my out-port ^^'


The other thing;

1; [http://pastebin.com/m575b50b8](http://pastebin.com/m575b50b8)

2; Nothing at all happens, just a new prompt.

3;  Wants me to accept install:
```

The following NEW packages will be installed:
  linux-headers-2.6.28-15 linux-headers-2.6.28-15-generic linux-image-2.6.28-15-generic linux-restricted-modules-2.6.28-15-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-restricted-modules-generic
4 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 34.8MB of archives.
After this operation, 173MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

[B]
Also; I'd really want you to explain what the commands do, I'm a learner ;)[/B]

---

