---
title: "/cdrom is not my cd-rom?"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by gatdammit on 2007-06-07
I keep getting this message at the bottom when I try sudo apt-get install build-essential.

The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8050kB of archives.
After unpacking 33.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

so I put the Cd in the drive and it autoplays.  I go back to the terminal and press enter and the last three lines keep showing up.  is my /cdrom not mounted?  I'm totally new and totally stuck.  I can't figure it out.  Help is greatly appreciated. Thanks.

---

### Post by Outrunner on 2007-06-07
Well, it looks like it wants to install from CD. Are you connected to the internet? Anyway, you'll need to edit your sources.list

```
gksudo gedit /etc/apt/sources.list
``` 

And comment out( with an #) the lines about cdrom(usually the first two)

Then update
```

sudo aptitude update
``` and try installing again.

---

### Post by mismis on 2007-06-07
edit your /etc/fstab file

find the line that goes like
/dev/s* /media/cdrom0 ****

change to 

/dev/cdrom /media/cdrom0 *****

that should work.

---

### Post by gatdammit on 2007-06-08
Thank you guys!

---

