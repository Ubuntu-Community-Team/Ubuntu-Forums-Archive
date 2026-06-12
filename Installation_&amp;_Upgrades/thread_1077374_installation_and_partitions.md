---
title: "installation and partitions"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by tudor_victor on 2009-02-22
hello

I recently decided to switch as permanently as possible from windows to linux. I freed a 300 gig hard disk and installed Ubuntu 8.10

I only made 2 partitions on the whole drive (actually the installer automatically allocated a swap of 5.8 gig and the rest is for the OS)

I read somewhere that there should be a separate partition for the /home directory.

Why? is it so program settings are kept if you install a new version of linux? I assume the user files will not be wiped if I install the next version of ubuntu.

Considering I already installed the OS, is it still possible to create another partition, and copy&mount /home on it?
if so, how much space should I allocate for it?

Should /home be used for all my user files (movies, music etc) and the rest only for OS and software?

---

### Post by kahlil88 on 2009-02-22
I just use the same partition for everything myself. Creating a separate home partition probably reduces fragmentation a little bit, but in the end I think it probably over-complicates things. For example, what happens when you don't have enough hard drive space to install more programs, or when your home partition gets to be too full?

---

### Post by WatchingThePain on 2009-02-22
Hi,

You don't need a seperate partition for the home directory but it's better if you have it like that. The reason it's better is in case your boot record gets messed up you can restore data from the seperate home directory.
Almost all my main directories are on seperate partitions.

It's easier to put everything in one partition but seperate is safer.

---

