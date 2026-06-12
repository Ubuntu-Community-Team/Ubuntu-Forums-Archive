---
title: "Cant define root system on installation"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by Andrewz09 on 2009-02-26
Hello
I am new to Ubuntu and Linux overall
now i download and made a CD
ran with it as normal windows installation
I got a small 30GB Partition i want Ubuntu to be on
and im using windows Vista on one of my other partitions.
now, during installation i came to the stage on which i have
to choose the location to where i want Ubuntu to be installed.
So i got:
/dev/sda
/dev/sda5 type:ext3 mount point:blank size: 30GB
and some more /dev that are my other partitions.
So as you may figured the 30GB one is the one im interested in
but when i click on it, and then press "Next" it says:
"No root system is defined. Please correct this from the partitioning menu."
Help >_<

---

### Post by albandy on 2009-02-26
in partition /dev/sda5 you have to edit properties and define it as / in the mount option

---

### Post by Pumalite on 2009-02-26
Have to plant an '/' where is says 'mount point'

---

### Post by Andrewz09 on 2009-02-26
Ok, i installed Ubuntu
but here are 2 questions:
1. During the installation i was asked to created "Swap" partition.
what is it used for? (i gave it 10GB, hope its enough)
2. How can i make a multi boot screen so that i can choose from logging
into Ubuntu or into Windows Vista?

---

### Post by albandy on 2009-02-26
yes it's enought, but the same size as your ram is enought too.
Swap partition is for caching memory pages in disk, when you don't have enought RAM the swap partition is used.

---

### Post by Pumalite on 2009-02-26
If it's a Laptop; make /swap 1.5 times your RAM if you want to hibernate

---

