---
title: "ati radeo x300, driver will not install..."
date: 2005-08-08
forum: Hardware &amp; Laptops
---

### Post by shockertwin on 2005-08-08
ok so i download the drivers and here is my problem.
> 
~/Desktop$ ./ati-driver-installer-8.14.13.run
bash: ./ati-driver-installer-8.14.13.run: Permission denied
~/Desktop$ sudo ./ati-driver-installer-8.14.13.run
sudo: ./ati-driver-installer-8.14.13.run: command not found


Because we dont use su -root any more, the driver installer wont work...

---

### Post by PeP on 2005-08-08
maybe

```
sudo  ./ati-driver-installer-8.14.13.run
```

or maybe not, you might prefer adding the restricted sources in /etc/apt/sources.list
then

```
sudo apt-get install linux-restricted-modules-2.6.10-5.386
```

(replace 2.6.10-5xxx by your kernel version)
if you don't know your kernel version, just ask:

```
uname -a 
```

if it is not 2.6.8.xxx or 2.6.10.xxx you won't have restricted modules, so first change to one of these kernels:

```
 apt-get install linux-image-2.6.10-5.386
```
where you replace 386 with your arch. (686 on a modern pc, 686-smp for a bi-processor, something else for apple or the 64 bit ubuntu)

---

### Post by brighton on 2005-08-09
could be 

sh ati-driver-installer-8.14.13.run 

as root

---

### Post by PeP on 2005-08-09
[QUOTE=brighton]could be 

sh ati-driver-installer-8.14.13.run 

as root[/QUOTE]
under ubunto you have no root with the default instalation, so that you use sudo to launch restricted programs.
-> sudo sh  ati-driver-installer-8.14.13.run 

this is in fact _more_ difficult,
you have to download it and update it manually each time they make a new release. Wich suppose you stay informed.

apt-get will update and patch it automatically, if you change your kernel your system will remain coherent (since you must the above script each time you update your kernel ) ...

apt also avoids compilation/installation problems.

---

### Post by zho40 on 2005-08-11
What kernel version are you running?  If you are using 2.6.11 or higher AGP is addressed different than in older kernels.  If you have a newer kernel you need to patch the ati driver before it will build.

---

