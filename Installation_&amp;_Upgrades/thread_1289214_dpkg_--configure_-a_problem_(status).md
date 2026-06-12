---
title: "dpkg --configure -a problem (status)"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by Michele Iurillo on 2009-10-12
Hi to everyone.. I have some problems with DPKG I can update because:
(I have spanish ubuntu)
yuri@ubuntu:~$ sudo dpkg --configure -a
[COLOR=Red][B]dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/status' cerca de la línea 11 paquete `xserver-xorg-input-vmmouse':
 campo de detalles de fichero `Size' no permitido en el fichero de estado[/B][/COLOR]

I have try to remove status file and apt-get update but don't run.

Thanks a lot

Info about my system:
Dell Inspiron 9400 2gb Ram
Ubuntu 9.04 updated from 8.01

-----------------------------------------------

if I try to apt-get I have this result

yuri@ubuntu:~$ sudo apt-get update
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release.gpg
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                 
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                           
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Packages  
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Sources   
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Sources
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources       
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Sources
[COLOR=Red]**E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. **[/COLOR]
yuri@ubuntu:~$

---

### Post by sisco311 on 2009-10-12
try:
```

sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
sudo dpkg --configure -a
sudo apt-get update

```

---

### Post by bruno9779 on 2009-10-12
you could go into synaptic package manager/edit/fix broken packages try that and see what happens.

By the way, I don't think that deleting the status file was a good idea

---

### Post by Michele Iurillo on 2009-10-12
The first thing that I've do was rm that file in this case I've this:

yuri@ubuntu:~$ sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.back
[sudo] password for yuri: 
yuri@ubuntu:~$ sudo rm /var/lib/dpkg/status
yuri@ubuntu:~$ sudo apt-get update
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release.gpg
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release            
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages      
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Packages  
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Sources   
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Sources
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Sources
**[COLOR=Red]E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema.[/COLOR]**


and then

yuri@ubuntu:~$ sudo dpkg --configure -a
dpkg: fallo al abrir el fichero de información del paquete `/var/lib/dpkg/status' para leer: No existe el fichero ó directorio
yuri@ubuntu:~$ 

--------------

so the status contain these lines (I put here only firsts)

Package: xserver-xorg-input-vmmouse
Priority: optional
Section: x11
Installed-Size: 128
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1:12.5.1-4ubuntu5
Replaces: xserver-xorg (<< 6.8.2-35)
Provides: xserver-xorg-input-4
Depends: libc6 (>= 2.4), xserver-xorg-core (>= 2:1.5.99.901), mdetect
Size: 18078

dpkg say to me that the problem is in SIZE in line 11

[COLOR=Red][B]Line 10 Depends: libc6 (>= 2.4), xserver-xorg-core (>= 2:1.5.99.901), mdetect
Line 11 Size: 18078[/B]
[/COLOR]
Some idea? Maybe I can change this value?

---

### Post by Michele Iurillo on 2009-10-12
If I run aptitude I've same problem

[IMG]http://lh3.ggpht.com/_d0vt0xwK7mU/StMh3I7jeyI/AAAAAAAAGZE/Xo0XJs5Rm3s/Aptitude.jpg[/IMG]

---

### Post by sisco311 on 2009-10-12
The status file is backed up daily in /var/backups. 

Unpack the backups:
```
sudo gunzip /var/backups/dpkg.status.*.gz
```

replace the file with the first backup:
```
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
sudo apt-get update
```

If it doesn't work, try the next one:
```
sudo cp /var/backups/dpkg.status.1 /var/lib/dpkg/status
sudo apt-get update
```

and so on...

---

### Post by Michele Iurillo on 2009-10-12
Thanks... no results: same problem

-----------------------------------------------
yuri@ubuntu:~$ sudo gunzip /var/backups/dpkg.status.*.gz
[sudo] password for yuri: 
yuri@ubuntu:~$ sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
yuri@ubuntu:~$ sudo apt-get update
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release.gpg
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg        
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Translation-es
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Translation-es
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release            
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release                     
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Packages                       
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages      
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Sources   
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Packages
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources       
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Sources
E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema. 
yuri@ubuntu:~$ sudo cp /var/backups/dpkg.status.1 /var/lib/dpkg/status
yuri@ubuntu:~$ sudo apt-get update
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release.gpg
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Translation-es
Ign [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Translation-es
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty Release        
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                           
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates Release
Obj [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                            
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Packages  
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty/multiverse Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/main Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/restricted Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/universe Sources
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Packages
Obj [http://es.archive.ubuntu.com](http://es.archive.ubuntu.com) jaunty-updates/multiverse Sources
**[COLOR=Red]E: dpkg se interrumpió, debe ejecutar manualmente «sudo dpkg --configure -a» para corregir el problema.[/COLOR]** 
yuri@ubuntu:~$

---

### Post by sisco311 on 2009-10-12
try to run *sudo dpkg --configure -a* after replacing the file with the backup:

```
sudo cp /var/backups/dpkg.status.1 /var/lib/dpkg/status
sudo dpkg --configure -a
sudo apt-get update
```

There should be 7 backup files: dpkg.status.0, dpkg.status.1, dpkg.status.2, ..., dpkg.status.6. 


You can also try to rebuild the file:
[http://ubuntuforums.org/showthread.php?t=474587]("http://ubuntuforums.org/showthread.php?t=474587")

post #4 and #5

---

### Post by Michele Iurillo on 2009-10-12
Now I've lost backup?

yuri@ubuntu:/var/lib/dpkg$ sudo gunzip /var/backups/dpkg.status.*.gz
gzip: /var/backups/dpkg.status.*.gz: No such file or directory
yuri@ubuntu:/var/lib/dpkg$

---

### Post by sisco311 on 2009-10-12
> **Michele Iurillo said:**
> Now I've lost backup?

yuri@ubuntu:/var/lib/dpkg$ sudo gunzip /var/backups/dpkg.status.*.gz
gzip: /var/backups/dpkg.status.*.gz: No such file or directory
yuri@ubuntu:/var/lib/dpkg$

No, the backups are already unzipped. Skip that step.

---

### Post by Michele Iurillo on 2009-10-12
Ok... but.. now I've problem in Line 2...

yuri@ubuntu:/var/lib/dpkg$ sudo cp /var/backups/dpkg.status.1 /var/lib/dpkg/status
yuri@ubuntu:/var/lib/dpkg$ dir
alternatives   cmethopt        info   statoverride    status.back  triggers
available      diversions      lock   statoverride-old    status-new   updates
available-old  diversions-old  parts  status        status-old
yuri@ubuntu:/var/lib/dpkg$ sudo dpkg --configure -a
dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/available' **[COLOR=Red]cerca de la línea 2 paquete[/COLOR]** `xserver-xorg-input-vmmouse':
 el valor para el campo `status' no está permitido en este contexto

more status

Package: xserver-xorg-input-vmmouse
[COLOR=Red]**Status: install ok installed**[/COLOR]
Priority: optional
Section: x11
Installed-Size: 124
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: 1:12.5.1-4ubuntu5
Replaces: xserver-xorg (<< 6.8.2-35)
Provides: xserver-xorg-input-4
...
...
...

So.. If I rm the status.. I can run dkpg.. If recover backups.. I've same problem...

I'm going crazy... last two events in my sys was

upgrading to flash player 10
upgrading last system

---

### Post by Michele Iurillo on 2009-10-12
> **sisco311 said:**
> No, the backups are already unzipped. Skip that step.

Yes... Some time I'm so stupid.. 
:-)

---

### Post by Michele Iurillo on 2009-10-12
NOT SOLVED

I'm still unsolved... but... I have try to make a update from menu.. Now Still updating..

---

### Post by Michele Iurillo on 2009-10-12
Not Solved Yet.. I've try update

[IMG]http://lh5.ggpht.com/_d0vt0xwK7mU/StNJ2Mdp8rI/AAAAAAAAGaA/JRNhtuBC4yw/Actual01.jpg[/IMG]

and after downloading appear this

[IMG]http://lh4.ggpht.com/_d0vt0xwK7mU/StNJ0TN3TKI/AAAAAAAAGZ8/sL-_XwXylfc/Actual02.jpg[/IMG]

---

### Post by Michele Iurillo on 2009-10-12
Still in problems... now with Available 

yuri@ubuntu:/var/lib/dpkg$ sudo dpkg --configure -aConfigurando daemontools-run (1:0.76-3) ...
grep: /etc/inittab: No existe el fichero ó directorio
grep: /etc/inittab: No existe el fichero ó directorio
grep: /etc/inittab: No existe el fichero ó directorio
grep: /etc/inittab: No existe el fichero ó directorio
grep: /etc/inittab: No existe el fichero ó directorio
Adding SV inittab entry...
cp: no se puede efectuar `stat' sobre «/etc/inittab»: No existe el fichero ó directorio
dpkg: error al procesar daemontools-run (--configure):
 el subproceso post-installation script devolvió el código de salida de error 1
Se encontraron errores al procesar:
**[COLOR=Red] daemontools-run[/COLOR]**


deamontools-run give me problem.. I've try to remove install from Synaptic but I cannot

Some Ideas?

---

### Post by Michele Iurillo on 2009-10-12
Just Solved...

I've make a backup of available files..
I've copy old version
I've remove old file

I don't know well how.. But now It's running.. the result in aptitude it's ok
[IMG]http://lh3.ggpht.com/_d0vt0xwK7mU/StNyjtsNCPI/AAAAAAAAGbk/WBK7Bt2pv6E/Aptiok.jpg[/IMG]

---

### Post by sisco311 on 2009-10-12
> **Michele Iurillo said:**
> Just Solved...



Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

