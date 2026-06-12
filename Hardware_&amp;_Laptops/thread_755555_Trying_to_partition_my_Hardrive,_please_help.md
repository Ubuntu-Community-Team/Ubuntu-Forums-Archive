---
title: "Trying to partition my Hardrive, please help"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by n2dabloo on 2008-04-15
I want to run XP and Ubuntu on the same laptop.  I have Gparted on cd and in my files.  I also have an XP Home Edition CD that I just purchased.  How do I do this?  I'm afraid I'll screw something up here.  I am a noob when it comes to this.  Thanks in advance.

---

### Post by sam_delta on 2008-04-15
hello, dont worry its an easy procedure

first of all if you havnt do so, ull need to install windows XP,
dont worry about g parted, you wont need it since you can manage partitions with the ubuntu installer

so you just install windows, then boot up with the ubuntu live cd, and click install
you will fill some information and when it comes to partitioning you select how much space do you want to keep windows with and the rest of it will be used by ubuntu

for example
if you install windows xp on a 80g pc, and you want 50 for ubuntu, then in the partition prompt in ubuntu installation you resize current windows partition to 30 and the installer will proceed using the rest (50g)

its pretty easy just follow the installation pormpts,

for more information you can go to 
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

or ask here :)

sam_d

---

### Post by Adreniline on 2008-04-15
Though, do note that you're advised to keep about 1GB open for a Linux Swap file.

So that would make it 3 partitions (though only two would be visible from within Ubuntu).

---

### Post by n2dabloo on 2008-04-15
> **sam_delta said:**
> hello, dont worry its an easy procedure

first of all if you havnt do so, ull need to install windows XP,
dont worry about g parted, you wont need it since you can manage partitions with the ubuntu installer

so you just install windows, then boot up with the ubuntu live cd, and click install
you will fill some information and when it comes to partitioning you select how much space do you want to keep windows with and the rest of it will be used by ubuntu

for example
if you install windows xp on a 80g pc, and you want 50 for ubuntu, then in the partition prompt in ubuntu installation you resize current windows partition to 30 and the installer will proceed using the rest (50g)

its pretty easy just follow the installation pormpts,

for more information you can go to 
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

or ask here :)

sam_d
Ok, I understand what you've said.  When I am in Ubuntu and insert the XP install CD nothing happens.  Shouldn't it give me an install screen?

---

### Post by bijeeshvs on 2008-04-15
Dont just worry its all just simple, first of all i dont know if you has any os installed on ur laptop. if it is so and u want to preserve your data then (most of the laptops comes preloaded with windows os but you have mentioned none) first install windows Xp on ur existing partition i mean windows partition, move ur essential data to another partition, if u have only one partition then there is two options 1) move ur essential data from that drive to any other medium like an external HDD and repartion the whole HDD 2) if u are no avail at this then u have to use some software like Partition Magic to convert ur free space to another partitions they have pretty good GUI and u  can easily make any type of partitions including linux partions while running it on windows. if you have the whole HDD at ur disposal then its pretty easy first decide how much space you require on both file systems if u use less space for linux then its no problem linux can easily recoganise and use windows partions so u have to boot from that windows cd first install ur system on the way xp will ask where to install and it will present you with a disk manager through which you can easily partion the HDD (windows CD will not work from Linux) make two primary partitions and create an extended partion using the whole space remaining, after installing windows on a primary partition install linux on the way linux will also ask u about where to install then choose manual hard disk partition and delete the second primary partition you created using windows (u can find it easily using the free space indicator bcoz in linux you will be presented by hda1 hda2 etc not like C D E drives ) create a root partition sparing at lest 512 MB or select the file system as ext3 and create a swap partition using the remaining free space and continue ur installation dont forget to install windows first otherwise u will not be able to boot linux coz windows will not recognize linux

---

### Post by sam_delta on 2008-04-15
> **n2dabloo said:**
> Ok, I understand what you've said.  When I am in Ubuntu and insert the XP install CD nothing happens.  Shouldn't it give me an install screen?

you first install windows and then ubuntu

to install windows you should boot from yourWindows CD, if your computer dosnt boot to the cd while you turn on the pc with the CD inserted, ull need to change the boot order under your computer BIOS in order to boot from the cd, usually by typiyng a comand while turning the cpu on (ex f12 ) it depends on the coputer

tell us how it goes

---

