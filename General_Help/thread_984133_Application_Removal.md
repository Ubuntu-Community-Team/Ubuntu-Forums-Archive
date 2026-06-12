---
title: "Application Removal"
date: 2008-11-16
forum: General Help
---

### Post by optimistique1 on 2008-11-16
Hi All, only been using Ubuntu for two days and very very bew to Linux...

I have an application called Gdeb that when I click on it it says 'missing option argument'.

I want to know how I remove this application from the application list as I already uninstalled the application.

Many thanks

Garry

---

### Post by soro2005 on 2008-11-16
Try System --> Preferences --> Main Menu

But if it's in the Menu, then it seems to me that it's no uninstalled correctly. You could open System --> Administration --> Synaptic Package Manager and look for it there.

In general, you want to install/uninstall ONLY programs that are in the Synaptic list of available programs, or if it absolutely has to be binary files whose name ends in .deb

These are handled by the package manager, and you should not have to remove their entries manually from the main menu. If you install, Windows style, whatever comes your way, you run the risk of screwing up your setup -- again Windows style.

By the way: Are you sure you are talking about Gdeb? It's a pretty essential system application.

---

### Post by optimistique1 on 2008-11-16
why does it say missing option argument' when I click the icon?

---

### Post by soro2005 on 2008-11-16
It is a little hard to tell what exactly is going on there. You don't normally run the program that comes with Gdeb on its own, but you run it on a software package you want to install. So perhaps it's complaining that there should be an argument when you try to start it dry, but there isn't.

Can you go to System --  Main Menu, locate the entry you are asking about, click on Properties, and post here what it says under "Command"?

---

