---
title: "[SOLVED] Cannot Mount NTFS drive?!"
date: 2008-08-16
forum: General Help
---

### Post by Ajuice on 2008-08-16
hey, i recently screwed up my windows installation (badly) and i was thinking i cold just use my ubuntu live cd and go in to recover my stuff like my music, and then back it up to my exernal drive.

well i boot up my live cd to and try to go in but i get the error saying it cannot mount the NTFS partiion because i didnt exit windoes properly (since it was really messed up i couldn't close properly)


it gives me the weird terminal commands, which i type in but they dont work


so i just wanna know, how do i get my crap off of my HDD before i wipe it and install ubuntu?


Sorry for my improper tech terms (if any)

Please Help me!!!

---

### Post by thestig_992 on 2008-08-16
> **Ajuice said:**
> hey, i recently screwed up my windows installation (badly) and i was thinking i cold just use my ubuntu live cd and go in to recover my stuff like my music, and then back it up to my exernal drive.

well i boot up my live cd to and try to go in but i get the error saying it cannot mount the NTFS partiion because i didnt exit windoes properly (since it was really messed up i couldn't close properly)


it gives me the weird terminal commands, which i type in but they dont work


so i just wanna know, how do i get my crap off of my HDD before i wipe it and install ubuntu?


Sorry for my improper tech terms (if any)

Please Help me!!!


For mounting the NTFS drive, i think that to force a mount you should use the following steps:
find the partition name of the windows drive:
```
sudo fdisk -l
```
look for the ntfs partition, the name should be something like hdb1, or sdb2 if ur using sata
then create a folder under /media to mount the filesystem in
```
cd /media
sudo mkdir windows
```
then finally to mount the filesystem
```
sudo mount /dev/(drive name) /media/windows -t NTFS
```
There should now be a drive on your desktop.
If you get an error from the last command, check out the manual for mount (man mount)<--lol that was bad naming) cause there might be something to do with mounting ntfs, as well as forcing it

remember that this wont allow you to boot widows again, it will just let you move stuff...

---

### Post by Ajuice on 2008-08-16
it says "Fdisk: invalid option -- 1"

then a bunch of other crap pops up...


this is after I type in "sudo fdisk -1"

EDIT: o wait, thats an L not a 1 lol

i'll try that lololol

---

### Post by Ajuice on 2008-08-16
ok well it seems to go well up until i have to type in "sudo mount /dev/(drive name) /media/windows -t NTFS"

then it says, "Mount: unknown filesystem typr 'NTFS'


err....

now what?

---

### Post by BTMark on 2008-08-16
> **thestig_992 said:**
> 
```
sudo mount /dev/(drive name) /media/windows -t NTFS
```
There should now be a drive on your desktop.


In my experience, using "NTFS" capped gives a "mount: Unknown filesystem type "NTFS", if this occurs, change NTFS to ntfs. Easy mistake!

---

### Post by Ajuice on 2008-08-16
> **BTMark said:**
> In my experience, using "NTFS" capped gives a "mount: Unknown filesystem type "NTFS", if this occurs, change NTFS to ntfs. Easy mistake!

i'll try that right now

---

### Post by Alex.peterson on 2008-08-16
Well its seems to be much important and useful suggestion. IT should be experienced.

---

### Post by thestig_992 on 2008-08-16
> **Ajuice said:**
> i'll try that right now

oops...i always forget that linux is case sensitive..soz

---

### Post by Ajuice on 2008-08-16
ZOMG!!!!

THANK YOU SOOO MUCH!!


i was able to go in and repair the crap i screwed up and i didnt even have to format my HDD!

now tomorrow im gonna install ubuntu alongside vista (shut up i like vista)

---

### Post by BTMark on 2008-08-16
Glad to see that you were able to solve the issue. You should mark the thread as [SOLVED]!

---

