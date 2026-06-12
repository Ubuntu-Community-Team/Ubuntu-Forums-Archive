---
title: "Synaptic Sux! Is there any alternative?"
date: 2008-09-13
forum: General Help
---

### Post by iampriteshdesai on 2008-09-13
I have weak internet connection and the fact that Synaptic has to regularly go scouting for keeping its info up to date is pissing. I get only 1 Gb worth of downloads per month and I hate it when synaptic eats into my pie. Is there any solution?

---

### Post by Infinite Indefinite on 2008-09-13
First backup the following file:

/etc/apt/sources.list

Then type in terminal:

sudo gedit /etc/apt/sources.list

And then put a hash (i.e. #) over every line starting with deb.

Synaptic will not bother you anymore.

---

### Post by iampriteshdesai on 2008-09-13
What will it do?
If it will stop syaptic from making sure itslibrries are OK, then thank you!

---

### Post by panayk on 2008-09-13
Edit /etc/apt/apt.conf.d/10periodic

Here's what the various options mean:

> "APT::Periodic::Update-Package-Lists=1"
- Do "apt-get update" automatically every n-days (0=disable)

"APT::Periodic::Download-Upgradeable-Packages=0",
- Do "apt-get upgrade --download-only" every n-days (0=disable)

"APT::Periodic::AutocleanInterval"
- Do "apt-get autoclean" every n-days (0=disable)

"APT::Periodic::Unattended-Upgrade"
- Run the "unattended-upgrade" security upgrade script
  every n-days (0=disabled)
  Requires the package "unattended-upgrades" and will write
  a log in /var/log/unattended-upgrades

"APT::Archives::MaxAge",
- Set maximum allowed age of a cache package file. If a cache
  package file is older it is deleted (0=disable)

"APT::Archives::MaxSize",
- Set maximum size of the cache in MB (0=disable). If the cache
  is bigger, cached package files are deleted until the size
  requirement is met (the biggest packages will be deleted
  first).

"APT::Archives::MinAge"
- Set minimum age of a package file. If a file is younger it
  will not be deleted (0=disable). Usefull to prevent races
  and to keep backups of the packages for emergency.

---

### Post by EvilMarshmallow on 2008-09-13
Yes, that's what you want.  Sources.list is all the places that synaptic is supposed to check.  # means "Comment" so any line that starts with # gets ignored.  It will do what you want.

---

### Post by Predator106 on 2008-09-13
But, er, wouldn't that remove all the sources, thus it would limit his range of packages?

---

### Post by panayk on 2008-09-13
> **Predator106 said:**
> But, er, wouldn't that remove all the sources, thus it would limit his range of packages?

Yes he wouldn't be able to install or upgrade any packages, ever, not even manually. By setting APT::Periodic::Update-Package-Lists to a sufficiently large number or 0, he would be able to decrease the frequency of automatic updates, but still be able to perform them manually.

---

### Post by Infinite Indefinite on 2008-09-13
> **EvilMarshmallow said:**
> Yes, that's what you want.  Sources.list is all the places that synaptic is supposed to check.  # means "Comment" so any line that starts with # gets ignored.  It will do what you want.
Precisely.

If he wanted, for whatever reason, to undo it, he could:

EITHER: replace the edited sources.list file with the backup.

OR: simply delete the relevant hashes in the edited sources.list file.

So with a few hashes, you can manage synaptic.

---

### Post by BenAshton24 on 2008-09-13
> Synaptic Sux!
Bit harsh, you'll make all the synaptic programmers turn emo! :P
but anyway, there isn't really a solution, downloading a package is gonna be just the same with synaptic as it is with any other package manager if u want to try some others then give "smart pm" a shot, a quick google should do it :D

Hope this helps,
Ben.

---

### Post by SunnyRabbiera on 2008-09-13
Synaptic is actually a great app in my opinion, but because you have a severely low limitation on your service I can understand frustration.
Switch ISP's thats what I would do.

---

### Post by javaJake on 2008-09-13
> **panayk said:**
> Yes he wouldn't be able to install or upgrade any packages, ever, not even manually. By setting APT::Periodic::Update-Package-Lists to a sufficiently large number or 0, he would be able to decrease the frequency of automatic updates, but still be able to perform them manually.

+1

This is the best option. You get your software, and you decrease bandwidth usage. :)

---

### Post by oldsoundguy on 2008-09-13
so it isn't Synaptic that sux .. it is the OP's internet connection.  Time to quit spending money on cigs, beer, and rockstar and upgrade that ISP!
That would solve the problem and not cripple his system.

---

