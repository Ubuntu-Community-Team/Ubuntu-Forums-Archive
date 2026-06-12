---
title: "Recomended installation packages please!!!"
date: 2009-02-12
forum: Installation &amp; Upgrades
---

### Post by sevenearths on 2009-02-12
I had a right nightmare a couple weeks ago.

I was doing an upgrade and right at the end compiz decided to freeze up and crash my system. After I rebooted I had to start metacity manually because I didn't have any window boarders (thats ok now thank god!)

All my little systems monitors on the panel disappeared, but I managed to get them back by reinstalling gnome-system-panel. I wondering if I can do the same for the following problems I am having:

[LIST=1]
[*]Can't lock the screen
[*]Screen saver won't work
[*]I can't have the window borders I want in compiz
[*]The buttons, sliders, checkboxes, etc... are all default in compiz (can't change)
[/LIST]

Does anyone know the packages for these?

---

### Post by sevenearths on 2009-02-17
anybody?

---

### Post by cariboo on 2009-02-17
Open System-->Administration-->Synaptic Package Manager and mark the unbutu-desktop for reinstallation. That should solve your problems.

Jim

---

### Post by sevenearths on 2009-02-18
> **cariboo907 said:**
> Open System-->Administration-->Synaptic Package Manager and mark the unbutu-desktop for reinstallation. That should solve your problems.

Jim

Yeah, tried that, no joy :(

---

### Post by sevenearths on 2009-02-18
can anyone help me, because this looks really ugly

---

### Post by konqueror7 on 2009-02-18
try
```
sudo apt-get install -f
```

---

### Post by sevenearths on 2009-02-24
```
arthur@arthur-laptop:~$ sudo apt-get install -f
[sudo] password for arthur: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
arthur@arthur-laptop:~$ 
```

:(

---

### Post by sevenearths on 2009-03-01
Anybody?

:(

---

### Post by whoop on 2009-03-01
Do you get any extra notification (like missing requirements) at System->Preferences->Appearance - Theme?

---

### Post by sevenearths on 2009-03-05
No. Everything looks fine in themes. :(

---

### Post by doudoufr on 2009-03-05
doing an upgrade when the problem appears ?

it sounds that you need to reinstall your graphic driver. :-)

---

### Post by sevenearths on 2009-03-13
> **doudoufr said:**
> doing an upgrade when the problem appears ?

it sounds that you need to reinstall your graphic driver. :-)

Yeah I tried that to no effect. What really weirds me out is that I can't lock my screen!

---

### Post by sevenearths on 2009-03-19
I think I'll wait till I need to do an upgrade since it's not really interrupting my workflow

---

### Post by sevenearths on 2009-10-29
got a new laptop. re-installed. all is good!

---

