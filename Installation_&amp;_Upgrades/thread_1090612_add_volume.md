---
title: "add volume"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by MarcusA on 2009-03-08
I have a dual boot Vista/Ubuntu, now I shrank an axtra 100GB from vistas volume to use in my ubuntu partition, but I don't have a clue on how to do this in Ubuntu :)

---

### Post by MarcusA on 2009-03-08
I hope its not too difficult :p

---

### Post by whoop on 2009-03-08
use partedmagic livecd or sudo gparted from ubuntu livecd

---

### Post by Neo_The_User on 2009-03-08
It's not. Open up terminal

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install gparted
gksudo gparted

```

Btw the update commands to update your system are in there even though you didn't ask.

Don't do sudo gparted like he said. gksudo gparted is much better. (It actually doesn't matter but everybody gives me a hard time about launching graphical apps using plain sudo)

---

### Post by MarcusA on 2009-03-08
:) ok thanx will try it out
What do I do exactelly in the program btw? lol yes I am a n00b..

---

### Post by MarcusA on 2009-03-08
Do I just click 'new' on the unallocated space and point out the same name as the partition of ubuntu on filesystem?

---

### Post by Neo_The_User on 2009-03-08
Don't take this the wrong way and I mean this in the nicest way possible, read the manual for gparted.

You can read up and dig through the documentation here: [http://www.gnu.org/software/parted/manual/](http://www.gnu.org/software/parted/manual/)

---

### Post by MarcusA on 2009-03-08
Okidoki, thanx

---

### Post by whoop on 2009-03-08
> **Neo_The_User said:**
> It's not. Open up terminal

```

sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install gparted
gksudo gparted

```

Btw the update commands to update your system are in there even though you didn't ask.

Don't do sudo gparted like he said. gksudo gparted is much better. (It actually doesn't matter but everybody gives me a hard time about launching graphical apps using plain sudo)

Isn't it unwise to edit the partition which gparted is running from?

---

### Post by Neo_The_User on 2009-03-08
> **whoop said:**
> Isn't it unwise to edit the partition which gparted is running from?

Well people always complain about them having to use a CD to fix it on so... I personally wouldn't. Probably won't let him anyway.

---

### Post by MarcusA on 2009-03-09
I managed it by using the liveCD

---

