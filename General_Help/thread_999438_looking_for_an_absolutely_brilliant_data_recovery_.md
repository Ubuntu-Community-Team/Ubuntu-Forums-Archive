---
title: "looking for an absolutely brilliant data recovery program"
date: 2008-12-01
forum: General Help
---

### Post by irish66 on 2008-12-01
Hi folks.
During many attempts at installing Linux MInt. my hard drive has been partioned, repartioned. repartioned and repartioned again probably. I have been using Stellar phoenix data recovery program in windows. Although it finds. they are wrongly named. Does anyone know of a better program.
M

---

### Post by PocketDog on 2008-12-01
The Ubuntu data recovery wiki page would probably be the best place to start [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by irish66 on 2008-12-01
Thanks very. I'll see if I can do it at some stage.
M

---

### Post by irish66 on 2008-12-02
Hi I'm using ubuntu live cd at the moment. 
my hard drive is unmounted and listed as dev/sda
It has two main partitions for LInux and windows.
But then the windows partition has 3 partitions in it.
So in partition editor,i see at the top dev/sda 232.88 gib
then below that two boxes side by side. In one is dev/sda1 98.28 gib and in the other dev/sda6 126.47 gib
then below that a list of partitions as follows
dev/sda1 ntfs) 
dev/sda2 extended
  dev/sda6 ext3
  dev/sda7 linux swap
  dev/sda5 ntfs
unallocated 5 gib 

hmm, that post didn't appear as it should.  sda6 sda7 and sda5 should have been indented. 
so method one
gparted
here is terminal output
ubuntu@ubuntu:~$ sudo swapoff -a
ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 1.8.9
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) rescue START 
END                                                 
Error: Invalid number.                                                    
(parted)


I am attempting to recover files from the  hard drive, which has been repartioned. What was once a windows drive
is now partioned into a windows/linux drive.
Ideally I would get a list of files and folders and then be able to choose which ones I would like to rescue and where I would like to place them. Even more ideally, the file name would correspond to the actual file content. Most of what I want to get are are mp3 files. BUt there is also a program. Well I can download the program again. What I really would like to recover is the files I created through the program.

,

---

