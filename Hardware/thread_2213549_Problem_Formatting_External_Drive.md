---
title: "Problem Formatting External Drive"
date: 2014-03-27
forum: Hardware
---

### Post by Bearly Able on 2014-03-27
I have a new external hard drive which I wanted to reformat to Ext4.  I can bring up the format dialogue and choose the correct options, but when I click on "Format" to proceed, nothing happens.  There is no error message; the window closes and the drive remains as it was.  I've tried reformatting a flash drive, with the same result, so the problem is not with the hard drive.

---

### Post by sudodus on 2014-03-27
Maybe the partition is mounted and must be unmounted before you can format it.

Try ***gparted***! It is available in all Ubuntu flavour desktop install isos, and can also be installed into an installed system
```

sudo apt-get install gparted
```

Start it with 
```
gksudo gparted
```
or from the menu system or from HUD.

It is rather easy to understand the graphical user interface of gparted. It is convenient to right-click ...

---

### Post by Bearly Able on 2014-03-27
Brilliant, thank you - that's solved it. :)

It's been so long since I needed to format anything, I'd forgotten all about gparted.

---

