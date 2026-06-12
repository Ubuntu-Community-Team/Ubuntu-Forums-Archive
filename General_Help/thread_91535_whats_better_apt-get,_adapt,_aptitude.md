---
title: "whats better? apt-get, adapt, aptitude?"
date: 2005-11-17
forum: General Help
---

### Post by tonysathre on 2005-11-17
i have read a lot of posts about ppl using adapt and aptitude, i myself always use apt-get.  the question i have is whats the difference, and which one is best, do they all have different features or do they perform the same basic tasks?

thanks for any clarity u may have for me

---

### Post by 23meg on 2005-11-17
Aptitude is the frontend to dpkg, which is the main package manager in Debian based distros. Aptitude includes commands such as apt-get, apt-cache, apt-key, apt-setup each of which have their own functions. Adept is KDE's GUI package manager, which in turn is a frontend to Aptitude. It just lets you perform Aptitude's commands in a visual way.

---

### Post by tabinin on 2005-11-17
Personally, even though I use KDE/Kububtu, I use Synaptic for package management.  Atitude, I have read, is not stable.  And, unless I am mistaken both Aptitude and Synaptic are just GUIs for apt-get.

---

### Post by kazu on 2005-11-17
aptitude is stable and **is** a command line. I think u mean adept.

In all case I think it's better to use command line. After, using apt-get system ou aptitude is quite the same. Maybe aptitude do the things a little cleaner sometimes ... but that's to be prove :p

---

### Post by mlomker on 2005-11-17
[QUOTE=kazu]aptitude is stable and is not a command line. I think u mean adept.
[/QUOTE]

You reversed those two.

The primary advantage of aptitude over apt-get is that it keeps track of the 'extra' packages that get installed when you install a package....it will then remove those unused packages if you remove the main package.  apt-get isn't smart enough to do that (neither is synaptic).

---

### Post by kazu on 2005-11-18
your right . ( in fact i was thinking aptitude is a command line but i put a not so stupid of me :p )

thak you for correcting that :p

---

### Post by bin on 2005-11-18
I must admit I found adept to be very fragile.

Synaptic works well and OK I know it installs a whole lot of gnome stuff - but it's worth it in the long run IMHO

in light

bin

---

### Post by Firetech on 2005-11-18
[QUOTE=23meg]Aptitude is the frontend to dpkg, which is the main package manager in Debian based distros. Aptitude includes commands such as apt-get, apt-cache, apt-key, apt-setup each of which have their own functions.[/QUOTE]
Eh, reverse that. APT (apt-get etc.) is the official frontend for dpkg, while aptitude is an alternate "client" that does what all apt-* commands does with just one main binary, and also includes a console "GUI". Aptitude does not include apt-get etc., it replaces them. (Try running "dpkg -L apt" (lists files in the "apt" package), "apt-cache show apt" (shows information about the "apt" package), "dpkg -L aptitude" and "apt-cache show aptitude" (same things for aptitude) in a terminal window.)

---

