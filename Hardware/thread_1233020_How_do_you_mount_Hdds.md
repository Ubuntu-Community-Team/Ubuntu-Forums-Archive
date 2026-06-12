---
title: "How do you mount Hdds"
date: 2009-08-06
forum: Hardware
---

### Post by frostyleo on 2009-08-06
Hi all

I habe just installed the lastest Desktop version. On a CF card in a Via Artigo A2000 with 2 x 1.5TB Hdds.

I can see the drives and they are not mounted how do i mount them

---

### Post by rslrdx on 2009-08-06
> **frostyleo said:**
> Hi all

I habe just installed the lastest Desktop version. On a CF card in a Via Artigo A2000 with 2 x 1.5TB Hdds.

I can see the drives and they are not mounted how do i mount them

so, you got 2 HDD besides the CF you installed the system on? if so, are they partitioned? what type of formating are you using? (EXT3, ntfs) 

You should be able to simply click the disk icon on the menu and it should mount automatically, otherwise you have to add the to your /etc/fstab file to be mounted automatically on boot.

btw, they are individual drives right? not raid ?

---

### Post by rslrdx on 2009-08-06
check out this thread, it shows how to identify and edit your /etc/fstab file.

[http://ubuntuforums.org/showthread.php?t=675528](http://ubuntuforums.org/showthread.php?t=675528)

let me know how it goes.

---

### Post by frostyleo on 2009-08-07
Thanks rslrdx


Being new to all this I'm doing it little by little. 

I have added/loaded partition editor. The drives have not been partitioned

Plans below

1. I plan to mirror the drives via software.
2. back up files from my mac and windows machines to here. So reading info on hdds as in what filesystem Etc.

---

### Post by rslrdx on 2009-08-08
mirror drives is raid, i havent dont that with linux in a long time, so i'm no help, but i can sugest Unison for the files backup, thats if you need them to be synced both ways, as in, on the linux box and the others, but if you just need/want the files copied over to the linux box as a pure file host, try rsync, its one way syncing though.

windows rsync client and server  (called DeltaCopy)
[http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp)

ubuntu
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)

Unison 
[https://help.ubuntu.com/community/Unison](https://help.ubuntu.com/community/Unison)

---

