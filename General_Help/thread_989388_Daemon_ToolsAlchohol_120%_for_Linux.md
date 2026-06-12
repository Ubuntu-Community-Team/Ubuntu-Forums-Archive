---
title: "Daemon Tools/Alchohol 120% for Linux?"
date: 2008-11-21
forum: General Help
---

### Post by Changturkey on 2008-11-21
Do similar applications exist in Linux?

---

### Post by sisco311 on 2008-11-21
[https://help.ubuntu.com/community/MountIso]("https://help.ubuntu.com/community/MountIso")

---

### Post by michande03 on 2008-11-21
if bin cue do

```
bchunk <file.bin> <file.cue> <file>.iso
```

then mount it via gmount iso or prefered application

---

### Post by stinger30au on 2008-11-21
virtualbox with xp loaded then go nuts

---

### Post by insane_alien on 2008-11-21
why the hell would you use a virtual machine to load an iso when you can just mount it natively?

---

### Post by TrD on 2008-11-21
[Acetoneiso](http://www.acetoneiso.netsons.org/)

---

### Post by Changturkey on 2008-11-21
Thanks all, I think I've asked this question before, sorry.

---

### Post by handy on 2008-11-21
> **Changturkey said:**
> Thanks all, I think I've asked this question before, sorry.

I don't think they all understand the full functionality of Alchohol 120%. :-)

---

### Post by Changturkey on 2008-11-21
> **handy said:**
> I don't think they all understand the full functionality of Alchohol 120%. :-)

Well nothing beats that, but you gotta live with it, until someone ports/reverse engineer/steal it or something. Same with OneNote.

---

### Post by K.Mandla on 2008-11-21
Moved to General Help.

---

### Post by Abraxis on 2009-01-08
So am I going to get yelled at for pointing at the elephant in the room?  What about copy protection? 

I've been searching for hours for a program to allow me to mount an ISO from my windows games, which are all copy protected.

So has anyone figured this out yet? and if so could you point me on my way?

and before you yell at me, These are my games, I bought them; legally.  And I am not talking about breaking any laws or forum codes here.

---

### Post by bodhi.zazen on 2009-01-08
> **Abraxis said:**
> So am I going to get yelled at for pointing at the elephant in the room?  What about copy protection? 

I've been searching for hours for a program to allow me to mount an ISO from my windows games, which are all copy protected.

So has anyone figured this out yet? and if so could you point me on my way?

and before you yell at me, These are my games, I bought them; legally.  And I am not talking about breaking any laws or forum codes here.

No matter how you obtained them we do not support cracking copy protection on these forums.

---

### Post by Abraxis on 2009-01-08
oh jeeze.

I agree and I'm not talking about trying to crack anything, you've misunderstood.

I'm looking for an accurate software simulation of a mounted volume via my cd/dvd-rom, like Daemon Tools or Alcohol 120%.  That's all.

I would appreciate it if you didn't jump to conclusions, you're making us all look bad.

---

### Post by jerome1232 on 2009-01-08
[http://cdemu.sourceforge.net/](http://cdemu.sourceforge.net/)

cdemu? creates virtual cd-roms which can have iso's mounted in them.

Then again you can just mount the iso using the mount command and tell wine that directory is a cd-rom.

---

### Post by Abraxis on 2009-01-08
thanks mate! this should work just fine

---

### Post by sedawk on 2009-01-08
The simplest way to use an iso is to mount it somewhere, e.g. check
the "loop" option of the mount command.
If I rememver right something like this works (if /iso exists):
```

sudo mount -o loop -t iso9660 /home/gamer/isopool/game.iso /iso

``` 

Sometimes this doesn't work. e.g. because the software looks for
a real disc drive and/or wants to get the volume ID of the disc.

For old DOS programs you can try DosBox, which has its own
CD emulation so you can use an iso instead of a real disc.
This works very often where simple mounting of the iso fails.

Wine doesn't come with a CD emulation for iso files.
But you can mount the iso (see above) and then add some information for
the mapped drive (e.g z: mapped to /iso). Actually this doesn't
work very well - inserting the real CD works much better with Wine.

Like mentioned in another posting above there is the "cdemu" project
which provides a (kernel) driver and some additional software to
simulate a cd disc drive using an iso image (or other images) on Linux.
This looks very promising. I gave it a few tries the last few months
but after a first successful trial (Ubuntu 7.x? kernel 2.4.x ?) I never
succeeded in making it work again with my newer Ubuntus.

---

### Post by hyperdude111 on 2009-01-08
gmountiso works and it is in the repos. If you go to gnome-look and nautilus scripts there is also an iso mounting script which is easy and lightweight.

---

