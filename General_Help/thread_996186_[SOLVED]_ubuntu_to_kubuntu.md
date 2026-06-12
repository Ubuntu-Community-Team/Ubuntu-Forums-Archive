---
title: "[SOLVED] ubuntu to kubuntu"
date: 2008-11-28
forum: General Help
---

### Post by frostyfrog on 2008-11-28
Hi folks , Ive installed ubuntu 8.04 as a dual boot with xp.
I would like to remove ubunta and install kubuntu 8.10 instead in the same partition . Any help about proceedure to do this would be appreciated.

---

### Post by OrangeCrate on 2008-11-28
First, add KDE:

[http://psychocats.net/ubuntu/kde](http://psychocats.net/ubuntu/kde)

Then, remove Gnome:

[http://psychocats.net/ubuntu/purekde](http://psychocats.net/ubuntu/purekde)

What you'll end up with, is a pure KDE environment on your existing installation.

Edit:

Just noticed that you want to go from 8.04 to 8.10.

Follow the instructions given above to get from Ubuntu to Kubuntu. Then when you're done converting to Kubuntu, simply go to Administration > Software Sources > Updates, and change the option at the bottom of that page from "Long term support releases only" to "Normal releases", and you'll find the option to upgrade to 8.10 the next time you run Update Manager.

As you requested, you'll have converted Ubuntu 8.04, to Kubuntu 8.10.

---

### Post by iKonaK on 2008-11-28
Just 2 lines:
```
sudo apt-get dist-upgrade
sudo apt-get install kubuntu-desktop
```;)

---

### Post by OrangeCrate on 2008-11-28
> **iKonaK said:**
> Just 2 lines:
```
**sudo apt-get upgrade**
sudo apt-get install kubuntu-desktop
```;)

Cool, but that doesn't take him from Ubuntu 8.04, to Kubuntu 8.10, as he requested, nor will it remove Gnome. Also, he'll have to change the Updates from LTS to normal, as I suggested, to get the distribution upgrade.

Edit:

I see that you corrected the command.

---

### Post by iKonaK on 2008-11-28
> **OrangeCrate said:**
> Cool, but that doesn't take him from Ubuntu 8.04, to Kubuntu 8.10, as he requested. He'll have to change the Updates from LTS to normal, as I suggested.
You're right, i forgot about that...:lolflag:
 but the commands are still applying  after the change of the update settings :)
EDIT:
or [COLOR=DarkRed]**better**[/COLOR]
```
sudo apt-get install kubuntu-desktop
```and then while still in gnome > **OrangeCrate said:**
> go to Administration > Software Sources > Updates, and change the option at the bottom of that page from "Long term support releases only" to "Normal releases"and then run the update manager and upgrade :)

---

### Post by OrangeCrate on 2008-11-28
> **iKonaK said:**
> You're right, i forgot about that...:lolflag:
 but the commands are still applying  after the change of the update settings :)
EDIT:
or [COLOR=DarkRed]**better**[/COLOR]
```
sudo apt-get install kubuntu-desktop
```and then while still in gnome and then run the update manager and upgrade :)

He'll have to remove Gnome prior to updating, to get to a pure Kubuntu 8.10.

From his original post...

> I would like to remove ubuntu and install kubuntu 8.10 instead in the same partition.

---

### Post by iKonaK on 2008-11-28
> **OrangeCrate said:**
> He'll have to remove Gnome prior to updating, to get to a pure Kubuntu 8.10.

From his original post...
How pure should be ? Can he just remove gnome after ? As far as i know all the versions have the same "base" - "buntu" , to get more flavors just install kubuntu-desktop, xubuntu-desktop, edubuntu-desktop, etc.

---

### Post by OrangeCrate on 2008-11-29
> **iKonaK said:**
> How pure should be ? **Can he just remove gnome after ?** As far as i know all the versions have the same "base" - "buntu" , to get more flavors just install kubuntu-desktop, xubuntu-desktop, edubuntu-desktop, etc.

Of course he can, I must have been thinking about something else as I typed that. Sorry.

---

