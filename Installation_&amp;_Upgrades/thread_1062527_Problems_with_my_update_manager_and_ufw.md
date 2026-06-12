---
title: "Problems with my update manager and ufw"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by ColombianBootloader on 2009-02-07
Hi there:(:(

Well, I thought that I was doing pretty good with my ubuntu skills (very limited!!!) but I have been experiencing two problems. First, I recently downloaded the ufw,which was opening up in ubuntu with no dramas, but now it does not seem to be working, I can click on under the system , administration menu then ufw and it does not show any window in my workspace. I just do not what is wrong, it does ask me for my administrator password,if I click the first time and then just do nothing. any suggestions?? If I try to do it again, then it will not do anything.

Second, (this is a real concern for me) the update manager is not working, I do the same thing as with ufw, (I go to the system menu, and under the administration menu I click on the update manager. well, nothing!!! it seems like it is not working either. any suggestions??

My ubuntu was working really sweet, and I have not done anything really different to my pc lately, I just installed some programs, like maxima, emacs, control lab, qucs and ufw. 

I am a new user of ubuntu and I just love it!!! but I need help with this so any suggestions or links are more than welcome

Cheers:p

---

### Post by kostkon on 2009-02-07
> **ColombianBootloader said:**
> Hi there:(:(

Well, I thought that I was doing pretty good with my ubuntu skills (very limited!!!) but I have been experiencing two problems. First, I recently downloaded the ufw,which was opening up in ubuntu with no dramas, but now it does not seem to be working, I can click on under the system , administration menu then ufw and it does not show any window in my workspace. I just do not what is wrong, it does ask me for my administrator password,if I click the first time and then just do nothing. any suggestions?? If I try to do it again, then it will not do anything.
What do you mean *ufw*?! *ufw* comes by default in recent versions of *Ubuntu* (and in 8.04, the version that you have). Do you actually mean [*gufw*]("http://gufw.tuxfamily.org/")?!

Try to run it from the terminal to see if it will give you any error messages. Open a terminal (*Applications &#8594; Accessories &#8594; Terminal*) and give:
```
gksudo gufw
```
post any errors here, if you like.

> **ColombianBootloader said:**
> Second, (this is a real concern for me) the update manager is not working, I do the same thing as with ufw, (I go to the system menu, and under the administration menu I click on the update manager. well, nothing!!! it seems like it is not working either. any suggestions??
Fist of all, in a terminal, again, give:
```
sudo apt-get update && sudo apt-get upgrade
```
and see if you'll get any errors.

---

### Post by ColombianBootloader on 2009-02-07
Hi there again..

yeah sorry, you were right it is gufw ;). so I did what you advised me and it did not work for gufw. the outcome was this. 

Code:

sasswillo@sasswillo-laptop:~$ gksudo gufw
Traceback (most recent call last):
  File "/usr/share/gufw/gufw.py", line 22, in <module>
    import gtk
ImportError: No module named gtk
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSsasswillo@sasswillo-laptop:~$ 

and for the update manager, well, it worked and this was the outcome

Code: 

sasswillo@sasswillo-laptop:~$ sudo apt-get update && sudo apt-get upgrade
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-es
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg          
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-es
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-es
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-es
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Leyendo lista de paquetes... Hecho
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se actualizarán los siguientes paquetes:
  gnome-power-manager jockey-common jockey-gtk linux-headers-2.6.24-23
  linux-headers-2.6.24-23-generic linux-image-2.6.24-23-generic linux-libc-dev
  python-apt ufw vim-common vim-tiny xserver-xorg-video-ati
  xserver-xorg-video-intel
13 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 31.7MB de archivos.
Se utilizarán 8192B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s

But at the end of everything, I got a error message, it is where is says ERROR DE TRATAMIENTO (sorry that is in spanish, I guess it is like TREATMENT ERROR??). This is what I got. 

Code:

Des:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-23-generic 2.6.24-23.48 [18.4MB]
Des:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main vim-tiny 1:7.1-138+1ubuntu3.1 [320kB]                                
Des:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main vim-common 1:7.1-138+1ubuntu3.1 [190kB]                              
Des:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main python-apt 0.7.4ubuntu7.4 [195kB]                                    
Des:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main ufw 0.16.2.4 [23.4kB]                                                
Des:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gnome-power-manager 2.22.1-1ubuntu4.1 [2235kB]                       
Des:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main jockey-gtk 0.3.3-0ubuntu8.2 [6710B]                                  
Des:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main jockey-common 0.3.3-0ubuntu8.2 [90.4kB]                              
Des:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-headers-2.6.24-23 2.6.24-23.48 [8140kB]                        
Des:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-headers-2.6.24-23-generic 2.6.24-23.48 [653kB]                
Des:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-23.48 [703kB]                                 
Des:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main xserver-xorg-video-ati 1:6.8.0-1ubuntu1 [466kB]                     
Des:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main xserver-xorg-video-intel 2:2.2.1-1ubuntu13.8 [337kB]                
Descargados 31.7MB en 6min32s (80.9kB/s)                                                                                   
Preconfigurando paquetes ...

[I]dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/available' cerca de la línea 25925 paquete `gvfs-fuse':
[/I]

Honestly, I do not know what is wrong. any more ideas??

Cheers;)

---

### Post by kostkon on 2009-02-09
There is the possibility that your first error is related to the second. Thus, open a terminal and do:
```
sudo apt-get clean
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

```
and see if everything goes fine.

---

### Post by ColombianBootloader on 2009-02-10
Thank your for your replay...

well, I did what you advised me and I got this outcome. I will put everything in order. However, I reckon I still have the problem I have highlighted the code where I guess the problem is. 

Code 

sasswillo@sasswillo-laptop:~$ sudo apt-get clean
[sudo] password for sasswillo: 
sasswillo@sasswillo-laptop:~$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 13 no actualizados.
sasswillo@sasswillo-laptop:~$ sudo dpkg --configure -a

[I]dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/available' cerca de la línea 25925 paquete `gvfs-fuse':
 EOF durante el valor del campo `Description' (falta nueva línea final)
[/I]
sasswillo@sasswillo-laptop:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/main Translation-es
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1) hardy/restricted Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg          
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-es
Des:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-es
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-es
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-es
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-es
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Des:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release [58.5kB]
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Obj [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Des:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages [416kB]
Des:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages [8001B]   
Des:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources [108kB]          
Des:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources [903B]     
Des:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages [163kB]     
Des:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources [36.2kB]     
Des:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages [27.7kB]  
Des:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources [4940B]   
Descargados 824kB en 19s (42.4kB/s)                                            
Leyendo lista de paquetes... Hecho
sasswillo@sasswillo-laptop:~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se actualizarán los siguientes paquetes:
  gnome-power-manager jockey-common jockey-gtk linux-headers-2.6.24-23
  linux-headers-2.6.24-23-generic linux-image-2.6.24-23-generic linux-libc-dev
  python-apt ufw vim-common vim-tiny xserver-xorg-video-ati
  xserver-xorg-video-intel
13 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
Necesito descargar 31.7MB de archivos.
Se utilizarán 8192B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
Des:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-23-generic 2.6.24-23.48 [18.4MB]
Des:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main vim-tiny 1:7.1-138+1ubuntu3.1 [320kB]
Des:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main vim-common 1:7.1-138+1ubuntu3.1 [190kB]
Des:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main python-apt 0.7.4ubuntu7.4 [195kB]
Des:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main ufw 0.16.2.4 [23.4kB]    
Des:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gnome-power-manager 2.22.1-1ubuntu4.1 [2235kB]
Des:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main jockey-gtk 0.3.3-0ubuntu8.2 [6710B]
Des:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main jockey-common 0.3.3-0ubuntu8.2 [90.4kB]
Des:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-headers-2.6.24-23 2.6.24-23.48 [8140kB]
Des:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-headers-2.6.24-23-generic 2.6.24-23.48 [653kB]
Des:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-23.48 [703kB]
Des:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main xserver-xorg-video-ati 1:6.8.0-1ubuntu1 [466kB]
Des:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main xserver-xorg-video-intel 2:2.2.1-1ubuntu13.8 [337kB]
Descargados 31.7MB en 11min33s (45.8kB/s)                                      
Preconfigurando paquetes ...
[I]
dpkg: error de tratamiento, en el fichero `/var/lib/dpkg/available' cerca de la línea 25925 paquete `gvfs-fuse':
 EOF durante el valor del campo `Description' (falta nueva línea final)
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/I]
sasswillo@sasswillo-laptop:~$ 

What could it be the problem?? 

Cheers:(

---

