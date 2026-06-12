---
title: "Remove files Via CLI"
date: 2011-04-14
forum: Hardware
---

### Post by Mj-egerton on 2011-04-14
Hi all, first sorry if this is posted in the wrong place, was unsure where it belonged

anyway... ive got a problem with my Ubuntu 10.10 system which appears to be that ive filled my hard drive and the system needs space

ive got the gnome power management settings error described here:
[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)

Ive tried all the things on there but no luck

im running a full partition install, no dual boot etc
i need to know how to access a folder in CLI and remove a file (film) The location for the file is a folder called "Movies" under "Documents" which is the default folders i believe. The film is called "Mr and Mrs Smith" and i can only access my pc through the Cmd Line interface 


Thanks

---

### Post by cwa on 2011-04-14
could you try opening a command prompt and type the following:

rm /path/to/file/filename

is your document/movie/filename in your home directory?

cwa

---

### Post by ajgreeny on 2011-04-14
Adfter you have logged in at the cli, ```
cd Documents/Movies
```will take you to the folder, ```
ls
``` will list all files in that folder and ```
rm filename.xxx
```will remove the file completely, not to the wastebasket, so make sure you get the name right, and don't forget linux is case sensitive.

To make sure you get the name right in that final command, type the first few letters of the file name and hit tab for auto-completion of the name.

However, are you sure that is the reason for the problem?  It seems a bit unlikely that a single film would fill a partition unless it is a small partition, and as you say it is not a dual boot, I wonder why you've run out of space.  What machine is it please? full specs, if you can, and partition arrangement may help.

---

### Post by Mj-egerton on 2011-04-14
Hi, thank you both for your replys

@Ajgreeny

im not completely sure of the total specs, it was a custom build

i am sure there is 1g RAM and a 157gb Hard drive, i ran the df -h command and it said 100% on the used space on the partition so i assumed i had used all the space

what else could it be?

(ps im a very basic linux user, sorry if i dont understand some things)

---

### Post by ajgreeny on 2011-04-14
That is a lot of space to fill, and I am a bit worried that just removing a single movie will be a very short lived solution to the problem.  Do you have a lot of video/movie files on disk, or thousands of photos and lots of music?

Can you show the output of your ```
df -h
``` command and also ```
sudo fdisk -l
```which may help a bit more.

---

### Post by technological on 2011-04-14
just use the rm command

---

### Post by Mj-egerton on 2011-04-14
> **ajgreeny said:**
> That is a lot of space to fill, and I am a bit worried that just removing a single movie will be a very short lived solution to the problem.  Do you have a lot of video/movie files on disk, or thousands of photos and lots of music?

Can you show the output of your ```
df -h
``` command and also ```
sudo fdisk -l
```which may help a bit more.


i just need to get the system back up and running with access to the GUI rather then CLI whereas i can delete at will from there, currently backing up my important files to my laptop, yes i backup my blu-ray films just incase they ever get damaged or scratched(personal use only no piracy or anything like that)
i was just looking into a new tb hdd when the system bugged out

i will get back to you with those figures for df -h and fdisk
but i did run a df -h and it told me the partition is 100% full

---

### Post by ajgreeny on 2011-04-14
OK, if you have a few blue-ray movies backed up to your hard disk Movies folder, I can see why you have filled it and now run out of any free space.

Use my original sequence of commands to remove one or more large files and you should then be able to get into the GUI and carry out whatever further actions you wish to.

---

### Post by Mj-egerton on 2011-04-14
Ive finnaly solved it, it appears to be hdd space was the issue got it all seems working fine again :) no time to order that new hdd :D


Thanks for your help ajgreeny can you give rep on this forum? i cant find it

---

### Post by ajgreeny on 2011-04-15
> **Mj-egerton said:**
> Ive finnaly solved it, it appears to be hdd space was the issue got it all seems working fine again :) no time to order that new hdd :D


Thanks for your help ajgreeny can you give rep on this forum? i cant find it
Sorry, I don't know what you mean at the end about "give rep"

---

