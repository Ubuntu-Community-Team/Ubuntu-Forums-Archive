---
title: "wlan on F-S amilo 1655g"
date: 2013-01-27
forum: Hardware
---

### Post by Trasherz on 2013-01-27
Hi all!
I have the same problem, like in this thread [http://ubuntuforums.org/showthread.php?t=1530962](http://ubuntuforums.org/showthread.php?t=1530962) (this is my manual), only i have xubuntu 12.04.
But actually Marvic with fsaa1655g cant help me. I make every step:
"1. Create a new folder: ~/Downloads/fsaa1655g

2. Download the [tarball]("http://www.marvec.org/amilo/fsaa1655g-kernel-2.6.26.tar.bz2") and untar in the said folder

3. Navigate to said folder via terminal:
*cd ~/Downloads/fsaa1655g*

4. Now install the modules via terminal:
*make && sudo make install*

5. Open (what I think is) your former "options"-file:
*sudo gedit /etc/modprobe.d/alsa-base.conf*

6. Scroll down untill you find the following line: "# Prevent abnormal  drivers from grabbing index 0". You should find some lines that start  with "options". Now add the following:
[B]options fsaa1655g radio=1
options ath_pci rfkill=0[/B]
... and close the window.

7. Now we'll add the module so it will load at startup, again using a terminal:
*sudo gedit /etc/modules*

8. At the end of the file, add the following:
**fsaa1655g**
... and close the window."

but nothing happens.
 The only difference is when i try to install fsaa1655g, i have next:
```
mama@Amilo:~/fsaa/fsaa1655g$ make && sudo make install
make -C /lib/modules/3.2.0-29-generic/build SUBDIRS=/home/mama/fsaa/fsaa1655g modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /home/mama/fsaa/fsaa1655g/fsaa1655g.o
/home/mama/fsaa/fsaa1655g/fsaa1655g.c:38:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[2]: *** [/home/mama/fsaa/fsaa1655g/fsaa1655g.o] Error 1
make[1]: *** [_module_/home/mama/fsaa/fsaa1655g] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
make: *** [default] Error 2
mama@Amilo:~/fsaa/fsaa1655g$ 

```looks like it doesnt work
So i try to install fsaa1655g-kernel-2.6.26, and the result is:
```
mama@Amilo:~/fsaa/fsaa1655g-kernel-2.6.26$ make && sudo make install
make -C /lib/modules/3.2.0-29-generic/build SUBDIRS=/home/mama/fsaa/fsaa1655g-kernel-2.6.26 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
[sudo] password for mama: 
su -c "install -d /lib/modules/3.2.0-29-generic/kernel/net/wireless/ && install -m 644 -c fsaa1655g.ko /lib/modules/3.2.0-29-generic/kernel/net/wireless/ && /sbin/depmod -a"

```Next i add to alsa-base.conf 
[B]options fsaa1655g radio=1
options ath_pci rfkill=0
[/B]like in manual, and steps 7 and 8 i make too.
Aaaaaand... nothing happens(

iwconfig
```
mama@Amilo:~/fsaa/fsaa1655g-kernel-2.6.26$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```need help!!

UPD
Maybe i need to switch on some driver or something else?
i`m not a linux user, this is my first try))

---

### Post by Trasherz on 2013-01-28
Maybe i need to use some earlier version of OS? Dbn there is a confirmation, that in 12.10 wlan works fine..

---

