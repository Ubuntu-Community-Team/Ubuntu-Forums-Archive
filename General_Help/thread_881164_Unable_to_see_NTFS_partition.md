---
title: "Unable to see NTFS partition"
date: 2008-08-05
forum: General Help
---

### Post by dsbogard on 2008-08-05
Dearest All---

I am a brand new beginner to Linux/Ubuntu, but am enjoying myself so far.


Anyhow, I can't get access to my previous windows vista (ntfs) partition.

I see it in gparted, and it is mounted as /windows.  however, it doesn't show up under computer or on the desktop.

I truthfully just want to be able to access my audio files / videos from my vista partition.

I have installed the NTFS configuration tool to no help.


Thanks so much

---

### Post by spiderbatdad on 2008-08-05
Do you mean you installed ntfs-config from synapatic package manager?
Did you go to the Applications>>System Tools menu and select it?

---

### Post by cgkades on 2008-08-05
Have you used a terminal in linux before? If you haven't, or just haven't in ubuntu, go to applications->accessories->terminal. 

Can you navigate to it using command line tools? Have you checked the directory /mnt ? 

OR you can try this...
Ok, i'm not on my linux box right now, so some of the names might be a little messed up. But if you go to places then computer, or system, try to get to your root directory / then try to find the windows folder there.

> **dsbogard said:**
> Dearest All---

I am a brand new beginner to Linux/Ubuntu, but am enjoying myself so far.


Anyhow, I can't get access to my previous windows vista (ntfs) partition.

I see it in gparted, and it is mounted as /windows.  however, it doesn't show up under computer or on the desktop.

I truthfully just want to be able to access my audio files / videos from my vista partition.

I have installed the NTFS configuration tool to no help.


Thanks so much

---

### Post by neilneil2000 on 2008-08-05
if it is mounted in /windows you should be able to use nautilus  (windows explorer) to navigate to that folder and get the stuff you want.

As a sanity check it may be worth openning a terminal window and typing ```
ls /windows 
```

this *should* give you the equivalent to "dir" for the ntfs partition.

If that throws back an error then its not mounted properly, otherwise you are on your way.

If you want to create a "shortcut" you can probably right click on the desktop and create a new "symbolic link" or just "link".

If not then you can do this from the command line as follows:

ln -s ~/Desktop/windows /windows

Happing Geeking

---

### Post by dsbogard on 2008-08-05
i did install the ntfs program----and i went to the root directory, but it is completly empty (no 'windows' in it)


thanks all for any thoughts.

---

### Post by cgkades on 2008-08-05
> **dsbogard said:**
> i did install the ntfs program----and i went to the root directory, but it is completly empty (no 'windows' in it)


thanks all for any thoughts.

you can try looking in the /mnt directory. Can you post a screenshot of GParted that says it's mounted in /windows?

---

