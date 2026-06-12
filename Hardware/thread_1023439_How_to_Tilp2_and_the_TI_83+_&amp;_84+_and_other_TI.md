---
title: "How to: Tilp2 and the TI 83+ &amp; 84+ and other TI Graphing Calculators (USB Link)"
date: 2008-12-27
forum: Hardware
---

### Post by RU-In? on 2008-12-27
There are a lot of people who have this issue w/ Ubuntu and there TI 83/84 Graphing Calculators with USB cables such as the Silverlink and the Direct Link cables.  

This is what I did to get tilp2 working on my Intrepid (32bit) install...

1. If you still have the tilp2 (and dependencies) installed from the repos, open synaptic and remove them.

2. Then goto this site and get the packages needed...

**[http://repo.calcforge.org/debian/i38...n/binary-i386/](http://repo.calcforge.org/debian/i38...n/binary-i386/)**

NOTE: For a description of each package, click on the 'Packages' link in the directory at this site, you
can download the description file by downloading 'Packages.gz' file)

For this workaround, download the following packages and install them in the order listed...

[B]libticonv3_1.1.0-1_i386.deb
libtifiles2-5_1.1.1-1_i386.deb
libticalcs2-7_1.1.3-1_i386.deb
libticables2-1_1.2.0-1_i386.deb

gfm_1.02-1_i386.deb
tilp2_1.12-1_i386.deb
[/B]
NOTE: I installed all of these in the order listed above (just double click them and deb package manager will open)

3. After successful install of the above packages you will have to open a terminal and run tilp as sudo

$ sudo tilp



Thats it for now, you can add them to your menu if you like, use 'gksudo tilp' for the command (or 'gksu tilp') whichever... :)


NOTE: Also 'Gfm' (Group File Manager) will run as regular user, just type 'gfm' in a terminal (no quotes ). It is a file grouper/ungrouper for the TI backups



Good luck to all, hope this get some linking with your TI Calculator running, Tilp2 will also support more that just the TI 83+/84+ as well.

Tilp2 homepage:
**[http://lpg.ticalc.org/prj_tilp/](http://lpg.ticalc.org/prj_tilp/)**

**If someone knows how to get this working further, mainly being able to run it as normal user, then please post... :)

---

### Post by Dynaflow on 2009-01-28
Note that the link to repo.calcforge.org/... above is malformed.  The actual address is [http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/](http://repo.calcforge.org/debian/i386/dists/stable/main/binary-i386/)

---

### Post by Thirtysixway on 2009-02-08
I keep getting an error when trying to view my screen or anything
```
KCrash: Application 'tilp' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

```

Does this only work if I have kde or something?

---

