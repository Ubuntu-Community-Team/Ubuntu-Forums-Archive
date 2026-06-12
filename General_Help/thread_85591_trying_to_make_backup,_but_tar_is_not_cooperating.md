---
title: "trying to make backup, but tar is not cooperating"
date: 2005-11-03
forum: General Help
---

### Post by GreyFox503 on 2005-11-03
This is probably one of those problems where the answer is staring me right in the face,  I'm just not seeing it.  I'm trying to make a system backup using a simple tar command to create a gzipped archive.  The exact command is:

```
sudo tar cvpzf backup_11_03_2005.tgz / --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/opt/games --exclude=/home
``` 

The problem is that after running for a few seconds, I see it diving right into my /mnt folder trying to backup a bunch of stuff I don't want (including the backup itself, considering my working directory is /mnt/hdb2)

I've tried a few variations on the syntax but I can't get it to exclude the directories I want.  The odd part is that I used to run this exact same command on Hoary, and it did what I expected it to.

Any terminal commandos out there know the solution?  Thanks for looking.

---

### Post by RAOF on 2005-11-03
I **think** you need to have all the --excludes before the directory you want to back up, namely /

Have you tried
```
sudo tar cvpzf backup_11_03_2005.tgz --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/opt/games --exclude=/home /

```
?

---

### Post by mykey on 2005-11-03
best you make a file with all the patterns to exclude - check the reference here - [http://www.gnu.org/software/tar/manual/](http://www.gnu.org/software/tar/manual/)

---

### Post by bionnaki on 2005-11-03
[QUOTE=GreyFox503]This is probably one of those problems where the answer is staring me right in the face,  I'm just not seeing it.  I'm trying to make a system backup using a simple tar command to create a gzipped archive.  The exact command is:

```
sudo tar cvpzf backup_11_03_2005.tgz / --exclude=/proc --exclude=/lost+found --exclude=/mnt --exclude=/opt/games --exclude=/home
``` 

The problem is that after running for a few seconds, I see it diving right into my /mnt folder trying to backup a bunch of stuff I don't want (including the backup itself, considering my working directory is /mnt/hdb2)

I've tried a few variations on the syntax but I can't get it to exclude the directories I want.  The odd part is that I used to run this exact same command on Hoary, and it did what I expected it to.

Any terminal commandos out there know the solution?  Thanks for looking.[/QUOTE]


see this HOW-TO: [http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by GreyFox503 on 2005-11-06
Thanks for all your replies!  All I had to do was move the / to the end of the command like that.

I wonder why the accepted syntax of the command would change like that across versions?  Maybe a new version of tar or something.

I originally got my backup method from Heliode's old post, but that applied to Hoary, not Breezy.


And on a side note:  holy cow!  After looking at that GNU page on the tar command... I had no idea how much documentation they had on ONE command.

---

