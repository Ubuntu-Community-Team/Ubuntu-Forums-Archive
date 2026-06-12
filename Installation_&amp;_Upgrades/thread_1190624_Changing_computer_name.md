---
title: "Changing computer name"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by kalaharix on 2009-06-18
Hi

I am restoring partition images of a particular installation on a number of machines. Not surprisingly they all end up with the same computer name as defined during installation. This confuses the network (and me) :)

Can somebody help with how to change the computer name?

rgds

---

### Post by _Purple_ on 2009-06-18
The name is in /etc/hostname and /etc/hosts. Change both of them using
```
gksudo gedit /etc/hosts /etc/hostname
```
Edit them both and save.

OR

go to System > Administration > Networking and edit from there.

---

### Post by kalaharix on 2009-06-18
Hi

Thanks for that. I still can't see how to do it from menus on 9.04 but editing the files does the trick.

rgds

---

### Post by coffeecat on 2009-06-18
> **_Purple_ said:**
> OR

go to System > Administration > Networking and edit from there.

> **kalaharix said:**
> I still can't see how to do it from menus on 9.04

The System > Administration > Networking utility was certainly there up until Intrepid, but has disappeared in Jaunty. Perhaps because everything that was in the networking app has now been integrated into Network Manager. Well, not quite everything - being able to change the hostname for example.

Hmm. I can't see any way to change the hostname from the GUI in Jaunty. Not a showstopper but not very helpful for newcomers to Ubuntu and/or Linux.

---

### Post by _Purple_ on 2009-06-18
> **coffeecat said:**
> The System > Administration > Networking utility was certainly there up until Intrepid, but has disappeared in Jaunty. Perhaps because everything that was in the networking app has now been integrated into Network Manager. Well, not quite everything - being able to change the hostname for example.

Hmm. I can't see any way to change the hostname from the GUI in Jaunty. Not a showstopper but not very helpful for newcomers to Ubuntu and/or Linux.

Thanks for pointing out that this utility is not there by default in Jaunty. Sorry, I forgot to mention that until Hardy, it was there by default. To use it in Intrepid or Jaunty, the package named gnome-network-admin has to be installed. 

```
sudo apt-get install gnome-network-admin
```

To the OP, the hostname will be under General tab(System > Administration > Networking) once you have installed the package.

---

### Post by coffeecat on 2009-06-18
> **_Purple_ said:**
> To use it in Intrepid or Jaunty, the package named gnome-network-admin has to be installed.

Thanks for the information. I should have realised it was a gnome package. Strange that Ubuntu have removed it from a default install. I've written a very simple apt-get script to automate the installation of all my favourite apps and utilities for whenever I do a new installation. I shall add gnome-network-admin forthwith.

---

