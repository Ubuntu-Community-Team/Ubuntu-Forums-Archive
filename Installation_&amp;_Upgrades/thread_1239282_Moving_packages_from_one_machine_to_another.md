---
title: "Moving packages from one machine to another"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by crenvy54 on 2009-08-13
Hello All,

I'm converting most of my 'puters from Windoze to Ubuntu. I have no 'net connection at home and must depend on intermittent connection when I travel to town (I'm in a 3rd world country so Internet is not so widely available). Fortunately I have this laptop that can d/l packages, updates, etc. However, my desktop machines do not have Internet and Ubuntu seems very dependent on an on-line mode to get these.

Is it possible for me to locate any packages I've d/l'd to this laptop and install them via USB drive or LAN to the desktop machine?

TIA!

- Casey

---

### Post by spvo on 2009-08-13
I don't think synaptic keeps a copy of the packages after they are installed.

I would install ubuntu frome the live cd on one of your computers.  Go into synaptic and select all the programs you want to be installed and all the updates, and tell it to generate an install script (it's in one of the menu options).  Then, next time you take your laptop into town, run the script and it will download all the necessary packages.

Once you have them just copy the packages to the computer and install them manually
```
sudo dpkg -i *.deb
```
The packages won't be deleted so you can install them on all the other computers you need to set up without downloading anything extra.

My internet connection at home is terrible, so I always do this anytime I install a new version of ubuntu.

---

### Post by Partyboi2 on 2009-08-13
Hi, you can also use a program called [[COLOR=Blue]Keyrx[/COLOR]]("http://keryxproject.org/") to get the packages from another machine that is connected to the Internet then take them back to your Ubuntu machine and install.

---

