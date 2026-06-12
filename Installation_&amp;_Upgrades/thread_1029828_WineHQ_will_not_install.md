---
title: "WineHQ will not install"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by rubixxx on 2009-01-03
The picture explains it all. I dl'd the latest wine for 8.04 hardy wine from: 

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

but i get that error mssg? :(

help!

thx!

---

### Post by liquidfunk on 2009-01-03
Do you have any other package manager open? It says that you do..

---

### Post by Pumalite on 2009-01-03
Only one apt-get process at the time.Maybe Synaptic open or the updater running?

---

### Post by rubixxx on 2009-01-03
i checked my processes, notthing like the sort that you guys have mentioned. its killing me!

---

### Post by Pumalite on 2009-01-03
Does Synaptic work?

---

### Post by rubixxx on 2009-01-03
uh...how would I know that? is it under processes? i'm still not completely fam with ubuntu sorry

---

### Post by Pumalite on 2009-01-03
System>Administration>Synaptic Package Manager

---

### Post by rubixxx on 2009-01-03
*sigh*

this is what I get...lol

I can't even open it!

---

### Post by ptn107 on 2009-01-03
Restart your computer and try again.

---

### Post by rubixxx on 2009-01-03
still get that err mssg.

---

### Post by tech0007 on 2009-01-03
Open a terminal and do:

```

sudo dpkg --configure -a

```

If it finishes with no error, run:

```

sudo apt-get update
sudo apt-get install wine

```

---

### Post by rubixxx on 2009-01-03
ok, i did everything you said. syn runs now, thanks.

so now is wine installed or do i have to go to synaptic and choose to install wine?

---

### Post by rubixxx on 2009-01-03
nvm, i got it.

thanks a lot, i really appreicate it.

---

