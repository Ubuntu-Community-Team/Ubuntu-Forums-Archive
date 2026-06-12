---
title: "I don't have permissions to copy from a CD?"
date: 2008-07-13
forum: General Help
---

### Post by Dansaycool on 2008-07-13
I'm having trouble copying some files from a DVD I made onto my Ubuntu Machine, I try copying the only folder on the DVD to my home directory and it pops up saying 'The folder "Term 2" cannot be handled because you do not have permissions to it.

I tried doing a

sudo chmod 777 /media/cdrom0 but it comes up saying its a read only filesystem?

I did try copying the folder to my iPod before I tried a DVD and it came up saying its a read only file system, I didn't fancy messing about with the mount options incase it ****** up my iPod..

---

### Post by solwic on 2008-07-13
> **Dansaycool said:**
> I'm having trouble copying some files from a DVD I made onto my Ubuntu Machine, I try copying the only folder on the DVD to my home directory and it pops up saying 'The folder "Term 2" cannot be handled because you do not have permissions to it.

I tried doing a

sudo chmod 777 /media/cdrom0 but it comes up saying its a read only filesystem?

I did try copying the folder to my iPod before I tried a DVD and it came up saying its a read only file system, I didn't fancy messing about with the mount options incase it ****** up my iPod..

I'm not sure if it would work, but did you try command line?  Open a terminal and try something like:

```
sudo cp -R /media/cdrom ~/home/yourusername/Term2
```

EDIT:  I'm not sure if it would need to be /media/cdrom or /media/cdrom/foldername.  Anybody clear that up?

---

