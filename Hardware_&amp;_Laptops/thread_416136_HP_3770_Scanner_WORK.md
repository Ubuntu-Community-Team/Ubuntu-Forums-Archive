---
title: "HP 3770 Scanner WORK"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by smileone on 2007-04-20
Tested with Ubuntu 7.04
How to install hp3770 driver
Before the installation procedure check our system that we have install 
[list]sane
xsane
libsane
sane-utils[/list]
[http://ftp.cyberbaladeur.fr/3770.tar.gz](http://ftp.cyberbaladeur.fr/3770.tar.gz)

download the package.

Extract this file, it contains two tgz files:
1)```
tar -xvzf 3770.tar.gz
```go into 3770 folder just create
2)```
cd 3770
```copy hp3770.tgz in main folder (/)
3)```
sudo cp hp3770.tgz /
```copy libsane.tgz in main folder (/)
4)```
sudo cp libsane.tgz /
```Now we can extract
5)```

sudo tar -xvzf hp3770.tgz
sudo tar -xvzf libsane.tgz

```6)```
sudo rm /hp3770.tgz
sudo rm /libsane.tgz
sudo rm /EULA.txt
sudo rm /README_hp3770.txt
```
Now modify dll.conf with root privilege
```
nano -w /etc/sane.d/dll.conf
```
add hp3770 voice
```
hp3770
```
Modify
```
$ sudo gedit /etc/sane.d/dll.d/hplip
```
add hp3770 voice
```
hp3770
```
Check your hp3770 scanner does it reconize with
```
$sane-find-scanner
```
With Ubuntu OS check 
```
nano -w /etc/udev/rules.d/45-libsane.rules
```
contains this 3 lines
```
# Hewlett-Packard|Scanjet 3770
SYSFS{idVendor}=="03f0", SYSFS{idProduct}=="2505", MODE="664", GROUP="scanner"
```

That's All.
:popcorn:
Now you can work with xsane application.

---

### Post by dbrunod on 2007-05-31
Hi !

I´ve follwed your steps. and got the scanner to work. But everythime I restart my computer I have to put the drivers in the folder again, because scanimage says error.

Any clues?
Kind regards,
Daniel:p

---

### Post by smileone on 2007-06-02
Hi,
which version of Ubuntu do you use?
I have tested this driver with Ubuntu 7.04.
Try to open xsane from the shell (ex gnome-terminal), and post you error .
;)

---

### Post by smileone on 2007-07-05
> **dbrunod said:**
> Hi !

I´ve follwed your steps. and got the scanner to work. But everythime I restart my computer I have to put the drivers in the folder again, because scanimage says error.

Any clues?
Kind regards,
Daniel:p

You can recompile libsane-extras.
Create new folder. (example SMILE]
```
cd SMILE
```
```
$apt-get source libsane-extras
```
```
$cd sane-backends-extras-<version>
```
```
cd backend
```
```
$nano -w Makefile.in
```
search line like 
EXTRA = sane_strstatus.lo ../sanei/sanei_init_debug.lo ../sanei/sanei_config.lo
and sobstitute with
EXTRA = sane_strstatus.lo ../sanei/sanei_init_debug.lo ../sanei/sanei_config.lo ../sanei/sanei_usb.lo
```
$cd ..
```
```
$dpkg-buildpackage -rfakeroot -uc -b
```
if you can't recompile check packages dependencies.
After recompile libsane-extras you can find deb file, install
```
$cd ..
```
```
dpkg -i libsane-extras-<version>.deb
```:p

---

### Post by pateta on 2007-11-08
Hi, please... any sugestion for install in 7.10 Gutsy Gibbon? No sucess for instal in this version of Ubuntu. Many thanks...

---

### Post by smileone on 2007-11-21
This hp3770 driver version doesn't work with the new version of libsane's library.
And cyberbaladeur don't release the source code! I think!

---

### Post by Tarmatt on 2007-11-21
Will it work on gutsy after a downgrade of libsane ?

---

### Post by robo2 on 2008-07-17
Using Ubuntu 8.04 I tried the scanner work according the post of Smileone.
Everything goes fine.
But when I tried: sudo gedit /etc/udev/rules.d/45-libsane.rules things don't go: because I miss in :etc/udev/rules.d '45-libsane.rules'.

Why should I miss that part in udev/rules.d

Miss I some package?

---

