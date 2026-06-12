---
title: "How to choose which programms to install at first system installation?"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2009-08-21
Hi,
i use ubuntu 9.04 but i don´t use lot of programs (pidgin, exiga, evolution). Normally, i deinstall them in synaptic, but there remain lot of other depended data files and programms (e.g. gnome-games-when i remove them i need to manually remove gnome-cards-data; with other  programms i have no clue wich dependencies i need to remove).

Is it possible to choose which programms i want to be installed at first installation (so that i can avoid to install e.g gnome-cards-data?
I install it with USB Stick on dell mini9.

---

### Post by MrWES on 2009-08-21
> **vickoxy said:**
> Hi,
i use ubuntu 9.04 but i don´t use lot of programs (pidgin, exiga, evolution). Normally, i deinstall them in synaptic, but there remain lot of other depended data files and programms (e.g. gnome-games-when i remove them i need to manually remove gnome-cards-data; with other  programms i have no clue wich dependencies i need to remove).

Is it possible to choose which programms i want to be installed at first installation (so that i can avoid to install e.g gnome-cards-data?
I install it with USB Stick on dell mini9.


From a terminal windows type:

```
sudo apt-get autoremove
```

That will clean up any left overs.

Bill

---

### Post by vickoxy on 2009-08-21
> **MrWES said:**
> From a terminal windows type:

```
sudo apt-get autoremove
```

That will clean up any left overs.

Bill

Well, i did that, but i still get for e.g. pidgin-data new updates... I mean does it really remove all dependencies?

---

### Post by ell02 on 2009-08-21
perhaps deborphan would be helpfull.

---

### Post by pawhtiobo on 2009-08-21
Hi :)

You can also install [this]("http://ubuntu-tweak.com/"), it has some tools to track broken packages/dependencies and configurations files that you don't need anymore.

see ya...

---

### Post by vickoxy on 2009-08-21
> **ell02 said:**
> perhaps deborphan would be helpfull.

What is that? Is that programm more useful as apt-get autoremove?

---

### Post by vickoxy on 2009-08-21
Ok,  so this means that i actually have to install all programs that are set on distros USB, and only after system installation can remove them?

> Hi

You can also install this, it has some tools to track broken packages/dependencies and configurations files that you don't need anymore.

see ya... 

Well, i just want something simple-not sure if i need that tool...

---

### Post by pawhtiobo on 2009-08-21
Its simmilar in some way, but got a GUI, and you can see witch packages, kernel and configuration files are no longer being used, just give it a try...if you don't like it, just remove it :D

see ya...

---

### Post by vickoxy on 2009-08-21
> **pawhtiobo said:**
> Its simmilar in some way, but got a GUI, and you can see witch packages, kernel and configuration files are no longer being used, just give it a try...if you don't like it, just remove it :D

see ya...

Ok, i installed it - can i have some > how to to find these old -not needed depencies?

To work something with packages i need to enter my password. Correct?

By "packages cleaning", after i enterred password i have these files: should i mark them and remove them-is that right place?

---

### Post by howefield on 2009-08-21
> **vickoxy said:**
> Is it possible to choose which programms i want to be installed at first installation (so that i can avoid to install e.g gnome-cards-data?

Might be easier to start with a minimal install and work up, rather than starting with the full install and working out what you don't need.

Something along the lines of this..

[http://distrowatch.com/weekly.php?issue=20081215#feature](http://distrowatch.com/weekly.php?issue=20081215#feature)

---

### Post by pawhtiobo on 2009-08-21
> **vickoxy said:**
> Ok, i installed it - can i have some  to find these old -not needed depencies?

To work something with packages i need to enter my password. Correct?

By "packages cleaning", after i enterred password i have these files: should i mark them and remove them-is that right place?

yes thats the right place :), you mark them to remove...

see ya...

---

### Post by vickoxy on 2009-08-21
> Might be easier to start with a minimal install and work up, rather than starting with the full install and working out what you don't need.

Something along the lines of this..

[http://distrowatch.com/weekly.php?is...081215#feature](http://distrowatch.com/weekly.php?is...081215#feature)

Well that was actually what i was looking, but i am newbie to linux so it seems to me that i could have lot of problems if i install it on my dell mini 9-drivers, some programms-i thought that there was some graphical interface in which you can select needed programs and over.
Thanks

---

### Post by vickoxy on 2009-08-21
Ok, so it seems that ubuntu-tweak removes some programms, but i have one question. I deinstalled *pidgin*, but *pidgin-data* are still in synaptic. Why it is not removed? Or some other programm needs this package?

Should i trust synaptic and leave behind all that it left after programm deinstallation?

I do not know if you understand my question? E.g. if i install *vlc*- i need to install 30-40 dependancies to run it. But if i choose to deinstall vlc, synaptic removes only vlc and maybe 2-3 other files.

---

### Post by pawhtiobo on 2009-08-21
> **vickoxy said:**
> Ok, so it seems that ubuntu-tweak removes some programms, but i have one question. I deinstalled *pidgin*, but *pidgin-data* are still in synaptic. Why it is not removed? Or some other programm needs this package?

Should i trust synaptic and leave behind all that it left after programm deinstallation?

I do not know if you understand my question? E.g. if i install *vlc*- i need to install 30-40 dependancies to run it. But if i choose to deinstall vlc, synaptic removes only vlc and maybe 2-3 other files.

I understand you question, well...i'm not sure, but Ubuntu Tweak should have also placed "pidgin data" in the list of removal, because is not in use anymore....about vlc, i think the Ubuntu tweak should see all the other files that are not in use, but i can't test it right now, because i'm using a Bill Gates Box...loll

see ya...

---

