---
title: "[SOLVED] Error 23 using rsync"
date: 2008-10-14
forum: General Help
---

### Post by _sAm_ on 2008-10-14
I want to use rsync to make backup of some folders to an external usb harddrive(mybook). My user is the owner of the mount point the disk use, and the source also belongs to my user(stored in home for my user). Both my home folder and the external harddrive has lots of free space.  I use Ubuntu Hardy. 

I have transferred a lot with no trouble. The problems starts when I add the flag -- delete for rsync, then I get error code 23. 

I just deleted one pdf in my home folder to see if rsync saw it and deleted it on my usb harddrive.

I have tried to google the problem but I cant find a solution. 

This command works:
rsync -avtr /home/sam/03_Dokumenter /media/disk/

This command gives me the error: 
rsync -avtr -- delete /home/sam/03_Dokumenter /media/disk/

Output from the terminal:
building file list ... rsync: link_stat "/home/sam/delete" failed: No such file or directory (2)

done

03_Dokumenter/00_Linux/Mine LinuxData/Terminal.odt



sent 91344 bytes  received 42 bytes  182772.00 bytes/sec

total size is 10886516291  speedup is 119126.74

rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]


Any suggestions?

---

### Post by geirha on 2008-10-14
You have a space between -- and delete. It should be one word; --delete

---

### Post by _sAm_ on 2008-10-14
O man, I feel like an idiot. Thanks for your help.

---

