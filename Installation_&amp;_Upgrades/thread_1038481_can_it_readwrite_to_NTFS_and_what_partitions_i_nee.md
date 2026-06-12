---
title: "can it read/write to NTFS and what partitions i need"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by gd6noob on 2009-01-12
**FIRST**
im almost done backing up my data onto a new larger drive and gona resize my partition on older drive so i can use linux/windows xp

since ubuntu can read NTFS can it also write to it?

i will be mostly just using ubuntu to surf the web, word processor and so on.. and i like to tons of videos on my computer so downloading and watching would probably be what i would mostly be doing on ubuntu

and also i would like to learn how to use a linux and try to stay away from MS OS's as much as possible

for windows it will be mostly gaming.

**SECOND**
since i have data i would like use with ubtunu, do i need to make

/
/home
/swap
and so on

or can i just make 1 or 2 and still be fine.
i have a 320gb drive and would give ubuntu 100gb and windows 100gb and the rest i leave for something else, or should i go 160gb unbuntu and 160gb to windows (i know its not a full % of the drive availible)

thanx for any help

---

### Post by blackened on 2009-01-12
Yes Ubuntu can read and write NTFS by default. 

The partition scheme is a matter of personal preference, but I would definitely suggest putting /home on a separate partition if only for ease of reinstallation should you trash something or wish to upgrade to the next version of Ubuntu without losing data in your home directory.

To my knowledge, an explicit swap partition is optional in recent versions of Ubuntu.

---

### Post by gd6noob on 2009-01-12
well i have a 320gb drive and at least 100gb would be for windows.. so i around 200 for ubuntu to use.. i would like to make least amount of partitions if possible

anyone recommend how i should set it up?

---

