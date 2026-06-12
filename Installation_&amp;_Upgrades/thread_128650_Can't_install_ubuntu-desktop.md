---
title: "Can't install ubuntu-desktop"
date: 2006-02-11
forum: Installation &amp; Upgrades
---

### Post by krigare on 2006-02-11
Hi,

I'm trying to upgrade from 5.04 to 5.10. Following the advice of [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes) I first tried to install the ubuntu-desktop package. It won't install--in fact, it's now a broken package. The problem seems to be a dependancy on ttf-kochi-gothic??!? It tries to read it off the install cd, no less. Is this dependancy really necessary? Is there any way to bypass it? Is there any other way to fix this?

Thanks!


On the command line I get:

```
steve@jubal:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
ubuntu-desktop is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: ttf-kochi-gothic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
steve@jubal:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ttf-kochi-gothic
The following NEW packages will be installed:
  ttf-kochi-gothic
0 upgraded, 1 newly installed, 0 to remove and 123 not upgraded.
1 not fully installed or removed.
Need to get 0B/4576kB of archives.
After unpacking 8012kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
in the drive '/cdrom/' and press enter


Preconfiguring packages ...
(Reading database ... 70895 files and directories currently installed.)
Unpacking ttf-kochi-gothic (from .../ttf-kochi-gothic_1.0.20030809-3_all.deb) ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /cdrom//pool/main/t/ttf-kochi/ttf-kochi-gothic_1.0.20030809-3_all.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/fonts/truetype/kochi/kochi-gothic-subst.ttf')
Errors were encountered while processing:
 /cdrom//pool/main/t/ttf-kochi/ttf-kochi-gothic_1.0.20030809-3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
steve@jubal:~$
```

In symantic it dies with:

```
E: /cdrom//pool/main/t/ttf-kochi/ttf-kochi-gothic_1.0.20030809-3_all.deb:  short read in buffer_copy (backend dpkg-deb during `./usr/share/fonts/truetype/kochi/kochi-gothic-subst.ttf')
```

---

### Post by Mustard on 2006-02-12
Something you might like to try is to comment out the CD rom entry in your /etc/apt/sources.list file by placing an hash character (#) in front of the line referring to your install CD.

```
sudo gedit /etc/apt/sources.list
#this will allow you to edit the file
#put a '#' in front of the line that refers to the install CD
#save the file

```

then..

```
sudo apt-get update
#update the package list from online repositories
```

After this, instead of looking for the package in question on your install CD, it should try to access it from the online repositories.  Hopefully this will be more successful for you. *fingers crossed* :)

---

### Post by krigare on 2006-02-12
That did it! It downloaded the packages, and they both installed just fine. Thank you so much!

---

### Post by Mustard on 2006-02-12
It looked like some type of read error from your CD too, so I would be wondering whether the problem was on the CD or in your CD drive. One would hope its on the install CD. :)

---

