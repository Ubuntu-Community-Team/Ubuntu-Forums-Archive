---
title: "EMERGENCY, Copied file over directory!"
date: 2008-08-08
forum: General Help
---

### Post by IMSargon on 2008-08-08
It was late - here's what I did:
In attempting to move a folder from my desktop to the home directory I use the command as root

hostname:/home/username/Desktop# mv Folder /home/*

Obviously, that's not what I meant to do. Now I have no home directory, and all my precious files are gone along with it. I'm sure my files are all still there, but how do I rebuild the directory now? 

-Sargon

---

### Post by iaculallad on 2008-08-08
To re-create you home partition, try this on your terminal:

```
sudo usermod your_user_name --home=/home/your_user_name
```

---

### Post by IMSargon on 2008-08-08
> **iaculallad said:**
> To re-create you home partition, try this on your terminal:

```
sudo usermod your_user_name --home=/home/your_user_name
```

The result is:

usermod: no changes

any other ideas?

---

### Post by IMSargon on 2008-08-08
I should mention - I'm using full disk encryption, so no external utilities (ie. boot disks)

-Sargon

---

### Post by IMSargon on 2008-08-08
I've now connected a large, external, ext2 formatted hard drive in anticipation of an inconvenient recovery.

Any advice would help. (besides backup more frequently and be more careful at the root terminal)

I think I'm calling into work sick today.

-Sargon

e2undel was unable to find ANY of the deleted files!!
Now I've logged out of my username, and logged back in as root.

---

### Post by IMSargon on 2008-08-08
HOLY MOLY, I found my files! Moved them back safe and sound. They had been moved into another user's home folder.

I'm not usually this bad. I need some sleep; I really do. For educational purposes, let's go over what happened here.

I entered the command:
#mv Folder /home/*
and both Folder and my user's home directory were moved into another folder in /home

Due to my misuse of the asterisk, my command was essentially saying:
#mv Folder /home/OtherUser

But why did my home folder move with it? Honestly, I still don't quite understand what my command did and why. I'd love for someone to help me understand the true meaning of the command I typed. Take your time - it's no longer a matter of life and death.

Thanks,
Sargon

---

