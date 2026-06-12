---
title: "Got Cuda Driver + Jaunty + Pyrit"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by andytof47 on 2009-11-05
Hi all I have the latest cuda driver installed for my 9500gt (after much stuffing around.... why isn't anything straightforward with this crap...... but it beats using window$ so I'll stop whining), but when I do a ```
pyrit list_cores
``` 
I still only get my cpu's detected. 

When I do this in Backtrack 4 PF it lists one cpu core and one graphics card core so does anyone know why my GPU isn't detected?

any help is much appreciated

---

### Post by andytof47 on 2009-11-05
ok, So compiling from source fixed the problems and I went from a benchmark of about 1200pmk's total for just CPU core 1 & 2

to 2325 pmk's so it was well worth it in terms of time.

how did I do this?
first ```
sudo apt-get install build-essential
```

I followed alot of howto's

Manually removed the envy-ng driver (this fixes the continual errors you get when you have conflicting nvidia drivers.) I love envy but it seemed to cause a conflict so.... I used it to get rid of the driver that comes with jaunty

[http://www.herikstad.net/2009/04/setting-up-cuda-environment-in-ubuntu.html]("http://www.herikstad.net/2009/04/setting-up-cuda-environment-in-ubuntu.html")

Disregard his thing about the removal of the file, just manual removal of the nvidia driver or envy-ng disable the driver

installed
```
sudo apt-get install python-dev
```
```
sudo apt-get install g++
```
```
sudo apt-get install build-essential libglut3-dev
```

then
```
chmod +x NVIDIA-Linux-x86_64-180.22-pkg2.run
```
```
CTRL-ALT-F1
```
then logged back in
```
./etc/init.d/gdm stop
```
```
./NvidiaInstaller.run
```

then 
```
/etc/init.d/gdm start
```


then followed the install instructions from pyrit
[http://code.google.com/p/pyrit/wiki/Installation](http://code.google.com/p/pyrit/wiki/Installation)

to get the SVN just install svn
```
sudo apt-get install subversion
```

then 
```
svn checkout http://pyrit.googlecode.com/svn/trunk/ pyrit_sv
```

version 190 at the time of this edit.

make sure your developer kit and toolkit for cuda are installed aswell then you can build the cpyrit package too, it's tweaked for nvidia cards

that was that... hope this helps

---

### Post by andytof47 on 2009-11-06
Lastly I just tried to replicate it on an identical machine and It wouldn't work...

I still needed to install ```
sudo apt-get install libssl-dev
```

---

### Post by akontiy on 2011-05-16
I do all done under the instruction but I still only get my cpu's detected. 
```

pyrit list_cores
Pyrit 0.3.0 (C) 2008-2010 Lukas Lueg http://pyrit.googlecode.com
This code is distributed under the GNU General Public License v3+

The following cores seem available...
#1:  'CPU-Core (SSE2)'
#2:  'CPU-Core (SSE2)'
#3:  'CPU-Core (SSE2)'
#4:  'CPU-Core (SSE2)'
#5:  'Network-Clients'

```
GTS 250 - version drivers 270.41.06
help!

---

