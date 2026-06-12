---
title: "How do i install .so files?"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by bavman on 2009-07-03
Im trying to get flash on my computer so i downloaded the regular one from the flash website, the .tar.gz. When i tried to install it from terminal it said i cant because it doesn support my archive system or something like that. Im running 64bit. So i found an alpha release for linux 64 on the adobe labs site but when i extract the tar.gz package all i get is this libflashplayer.so file. I dont know how to install it. Thanks for any help.

---

### Post by oldos2er on 2009-07-03
There's an install script here: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

 Or you can just copy the file to /usr/lib/mozilla/plugins

---

### Post by ddnev45 on 2009-07-03
You'll need to make a symbolic link (as root) in the /etc/alternatives/ directory that refers back to the libflashplayer.so file.

```
sudo ln -s libflashplayer.so /etc/alternatives/libflashplayer.so
```

If the non-free flash was installed by default from the repositories, that will first need to be removed with synaptic.

---

### Post by arushad on 2009-07-12
How to install Graphic driver, i've got two files dats 
sis_drv.la
sis_drv.so

---

### Post by oldos2er on 2009-07-12
> **arushad said:**
> How to install Graphic driver, i've got two files dats 
sis_drv.la
sis_drv.so

 Sis video drivers should already be installed, but if not, run
```
sudo apt-get update && sudo apt-get install xserver-xorg-video-sis
``` in a terminal.

---

### Post by CedSha on 2011-06-09
> **ddnev45 said:**
> You'll need to make a symbolic link (as root) in the /etc/alternatives/ directory that refers back to the libflashplayer.so file.

```
sudo ln -s libflashplayer.so /etc/alternatives/libflashplayer.so
```

If the non-free flash was installed by default from the repositories, that will first need to be removed with synaptic.

>> you can just copy the file to /usr/lib/mozilla/plugins
2011... Still works for me for Flash player 10 square 64 bits
without doing symbolic link...

Tks

---

### Post by nomko on 2011-06-09
> **bavman said:**
> Im trying to get flash on my computer so i downloaded the regular one from the flash website, the .tar.gz. When i tried to install it from terminal it said i cant because it doesn support my archive system or something like that. Im running 64bit. So i found an alpha release for linux 64 on the adobe labs site but when i extract the tar.gz package all i get is this libflashplayer.so file. I dont know how to install it. Thanks for any help.
 
The libflashplayer.so file doesn't need to be installed, just do this:
 
- open Nautilus
- click on Ctrl+H to make the hidden files/directories visible
- open the folder .mozilla
- open the folder firefox
- check if there's a folder called plugins
- put the libflashplayer.so file in the plugins folder

---

