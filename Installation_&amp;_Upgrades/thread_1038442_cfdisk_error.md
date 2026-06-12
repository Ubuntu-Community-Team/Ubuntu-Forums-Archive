---
title: "cfdisk error????"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by w1av on 2009-01-12
Hi!
I want to install Ubuntu on hdb3, my SLAVE hard drive, third partition. When I run Ubuntu from the CD, and start the terminal, I then invoke "cfdisk" to set up the disk and get THIS:

[B]FATAL ERROR: Bad primary partition 1: Partition ends in the final partial cylind
                          Press any key to exit cfdisk[/B]

I have a Win XP installation on HDA. HDB is a SECOND STORAGE drive with 3 partitions. Why do it get this error?  How can I fix the problem so I can install Ubuntu? Thanks :(

---

### Post by briandu on 2009-01-12
u did state cfdisk /dev/sdb right?   it defaults to /dev/sda   (or hda if IDE drives)

plus u need to datate which partition of more than 1 e.g. cfdisk /dev/sdc1

Rather use gparted as it is more intuitive.

To get it stste sudo apt-get install gparted then look under the admin panel.

---

