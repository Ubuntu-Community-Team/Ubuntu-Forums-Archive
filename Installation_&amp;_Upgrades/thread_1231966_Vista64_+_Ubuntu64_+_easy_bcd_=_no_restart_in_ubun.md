---
title: "Vista64 + Ubuntu64 + easy bcd = no restart in ubuntu"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by alexhore on 2009-08-05
[FONT=Tms Rmn][SIZE=2]Hi all, I am thinking this is going to be an easy fix but no matter how much I search I cannot find the answer so here goes.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]Trying to used easy bcd with the vista bootloader as grub bootloader wont work with my vista on raid0.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I have vista 64bit installed on my raid0 hard drive setup two drives showing as c under windows raid is on the mobo.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I installed easy bcd current version.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I installed osx on the second drive[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]Then I made three more partitions the end one is storage[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I installed Ubuntu in the middle two partitions one for files system and other for swap.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I selected in the advanced menu when installing to install grub on hard drive 2 partition 2 (it recognised the the main file system partition).[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]So just to summarise[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]hdd1 (raid0) windows vista64bit[/SIZE][/FONT]
[FONT=Tms Rmn][SIZE=2]hdd2 osx ubuntu swap storage[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I repaired the vista mbr and can boot in and out of vista fine.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I made entry's using bcd for osx and ubuntu.[/SIZE][/FONT]
[FONT=Tms Rmn][SIZE=2]("add an entry" selected linux named it and selected partition from list)[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I can now boot in and out of vista and osx fine.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]After my first boot of ubuntu I had to fix the mbr again? no operating system[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]After lots of messing around I have discovered I only smash the mbr when I use the restart option in ubuntu.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]So to summarise again I can boot in and out of all operating systems fine using shut down but restart in ubuntu seems to be writing to the mbr.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]I am guessing this will make sense to someone as the system has to write to mbr to tell the system to come back on but I don't really have a clue.[/SIZE][/FONT]
 
[FONT=Tms Rmn][SIZE=2]Any help will most defiantly be appreciated and I will follow up for others.[/SIZE][/FONT]
[FONT=Tms Rmn][SIZE=2]I have dropped this on both the ubuntu forums and neosmart forums.[/SIZE][/FONT]
[FONT=Tms Rmn][SIZE=2]Many thanks[/SIZE][/FONT]

---

### Post by alexhore on 2009-08-05
On the off chance someone is following this I have just realised there is a beta 2.0 easy bcd which I should be using.
As I am using the latest ubuntu I should not have even been able to boot as fix's are in 2.0.
Ill try tonight and update.

---

### Post by carpetbelly on 2009-08-05
I had issues with trying to work this out previously (now just on ubuntu and scrapped my vista not because of this though).

Firstly, yes, you do need EasyBCD2 for this to work. Then it's the neogrub option you want to chose to pick up the linux boot. Also, it's handy to boot into the ubuntu live cd to get the UUID for the linux partition. No need when ubuntu was installed to have installed grub though if you're using the neogrub bootloader (well, i found that to be the case after a few different tried and reinstalls, deletes, start again testing)... 
 
then using easybcd just amend your neogrub menu.lst to boot the kernal using the uuid and hey presto.

---

### Post by alexhore on 2009-08-06
Well that dint work. All I can asume is that becouse the MBR is on a raid setup linux screws it up when restarting as linux see's the drives as two seperate drives.
Thats on another asumption that linux writes to the MBR on restart.
:( O well, I will have to just use the shut down option and turn it back on with the power button for now grrrrrrr

---

### Post by carpetbelly on 2009-08-06
I reinstalled my system tonight (was bored) just to check this... ok, install vista, then install the other os'. I loaded grub onto the partition where i installed ubuntu (in the advanced options before finalising install). You dont have to load grub but you can if you wish. Then when it's installed you'll just boot into vista, fire up easybcd2, put a linux part on it, say grubs installed on the partition you installed it to and hey presto, when you reset you'll have a boot loader for vista and other os's... that will then in turn load the grub you installed on the linux partition. 

Or you dont install grub and neogrub it where you recreate menu.lst in xp and that acts as grub... cleaner but not quite as easy as you need to muck around with live cds to go get the UUIDs for the new drives.

---

### Post by alexhore on 2009-08-07
Hi there,  thats for the reply, my vista is sat on a raid0 array and so is the MBR/vista bootloader.
Spoke to a few IT guys at work and they all confirm Os's do write to the MBR when re-starting and becouse linux dose not recognise my raid0 it thinks I have two drives and writes on one of them only, the first, messing up the vista bootloader.
 
Options are...
 
1 Find some software that lets linux recognise raid0.
2 Move the MBR/vista bootloader over to the storage drive (none raid) and set that as the boot disk.
3 Edit Ubuntu so that it the restart comand just shuts it down instead
3 Leave it as it is and stop being soft.
 
Hummmmm, anyone know if 1,2 or 3 are possable?

---

