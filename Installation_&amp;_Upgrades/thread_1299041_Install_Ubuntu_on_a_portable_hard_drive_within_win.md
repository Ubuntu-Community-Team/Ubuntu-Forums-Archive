---
title: "Install Ubuntu on a portable hard drive within windows"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by elliotbeken on 2009-10-23
hi all i would like to install ubuntu on my portable hard drive so i can run it from within windows and not have to boot from the hard drive at a restart. 

is this possable ??

thanks

---

### Post by Mark Phelps on 2009-10-24
Basically -- no.  

A Wubi install (i.e., inside Windows) will allow you to install Ubuntu to the portable drive, but it will modify the boot.ini file on your hard drive and the registry there as well.

You will STILL have to boot from your hard drive in order to get the MS Windows boot selection menu containing Ubuntu.

---

### Post by the8thstar on 2009-10-24
Use VirtualBox or VMWare and store the Ubuntu virtual machine on the external drive. This way you can fire it up whenever you need. And that won't mess up your windows boot.ini file.

---

### Post by elliotbeken on 2009-10-26
thanks that sounds like a good idea but how would i do this. i have looked around the net and it seems like it cant not be done

---

### Post by RichardCL on 2009-11-17
> **the8thstar said:**
> Use VirtualBox or VMWare and store the Ubuntu virtual machine on the external drive.

This is exactly what I'm planning:)

Can I use the same remote hard disk on multiple machines e.g. run UbuntuVM on USB Drive from Windows laptop and Ubuntu desktop?

How much performance drop is to be expected in the host. My Windows Laptop is a Atom 260 with 2GB ram. Will there also be a performance drop in the host when Virtualbox is not running?

I assume the guest Ubuntu in Virtualbox from USB will be slower than contiental drift.

---

