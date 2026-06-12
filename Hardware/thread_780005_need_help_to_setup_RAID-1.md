---
title: "need help to setup RAID-1"
date: 2008-05-03
forum: Hardware
---

### Post by chekha on 2008-05-03
hello.

i am a new user with ubuntu 8.04.
i have a "HighPoint RocketRAID 100" controller.

and i need to install this driver on Ubuntu.
I have never installed driver manually on ubuntu.

i downloaded the "open source" driver from this page:
[http://www.highpoint-tech.com/USA/bios_rr100.htm](http://www.highpoint-tech.com/USA/bios_rr100.htm)

can someone help me? :confused:

---

### Post by ddrichardson on 2008-05-04
Download the open source driver at the bottom of the page and uncompress it (tar xvfz filename.tar.gz) then follow the instructions in the enclosed readme.txt

Where it says "1) Install kernel build tools (gcc, binutils, make, etc.)" you can cut through the mustard here by typing sudo apt-get install build-essential from the command line.

Unfortunately whoever wrote it didn't include a configure script which would tell you what you're missing before you build it.

There is further community documentation [here]("https://help.ubuntu.com/community/Installation/RAID1").

Mind you, they have got RedHat RPMS so you could use alien to convert then to DEB and install. That might be your easiest option.

---

### Post by chekha on 2008-05-10
hello again,

thank you for your reply.

i tried to download the Red Hat package:
[http://www.highpoint-tech.com/BIOS_Driver/rr100/Linux/372-redhat-v135-0822.tgz](http://www.highpoint-tech.com/BIOS_Driver/rr100/Linux/372-redhat-v135-0822.tgz)

and i have installed Alien.

how do i convert to .deb ?
i had a look on :
[http://howtoforge.com/converting_rpm_to_deb_with_alien](http://howtoforge.com/converting_rpm_to_deb_with_alien)

but i could not find any .rpm extension files within the archive.

? :confused:

by the way, my RAID-1 is just for storage of important files.
it does not contain the OS or system files.

---

### Post by ddrichardson on 2008-05-10
Sorry, I assumed that being RedHat it would be an RPM. tgz are compressed tar files and can be expanded by double clicking in Nautilus or by typing:
```
tar xvfz filename.tgz
```
There is a help file in the uncompressed folder.

---

