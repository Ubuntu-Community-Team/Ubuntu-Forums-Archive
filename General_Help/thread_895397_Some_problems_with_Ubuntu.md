---
title: "Some problems with Ubuntu"
date: 2008-08-20
forum: General Help
---

### Post by angeH on 2008-08-20
Hi

Have been using Ubuntu for a while now, but have recently noticed some problems occurring.  I realise that these could be in separate threads but wondered if anyone else was noticing the same and that they were actually all relating to the same issue:

1. Sound.  Seems like once I have started listening to sound from one place, such as Internet, I can't then get sound from anything else, such as any of the players for listening to music on the hard drive.

2. Gedit.  Feels like every time there is an update Gedit fails.  It will freeze while trying to open, even if being opened via a terminal.

3. Firefox.  Firefox is freezing a lot of the time now, tre greying out that I know comes from compiz.

4. Application menu.  Occasionally the Application menu freezes if I try to select an application.  It remains highlighted and I can't do anything else.

Anyone have any ideas?  It's getting to be a real problem as I need to reboot every few hours....I may as well use windows :(

USING Heron: 8.04

---

### Post by ad_267 on 2008-08-20
Are you using 8.04? For your first problem you can install libflashsupport package. This is an issue with adobe flash. I don't know about the other problems though.

---

### Post by angeH on 2008-08-20
sorry yes - i should have said I was using heron 8.04...I will try thi supdate thanks.

> **ad_267 said:**
> Are you using 8.04? For your first problem you can install libflashsupport package. This is an issue with adobe flash. I don't know about the other problems though.

---

### Post by Vivaldi Gloria on 2008-08-20
About sound:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by Kevbert on 2008-08-20
Regarding freezes - this could happen for a number of reasons.
I'd perform a memory check from the grub boot menu (memtest) as it's possible to run windows with faulty memory (though you'll occasionally get unexpected crashes).  
The greyed out screen can be a little annoying at times.  This is not necessarily compiz but can be due to heavy network traffic.
I'd also suggest you try running the following command in Applications-Accessories-Terminal
```
sudo apt-get install -f
```
in case you have any broken packages. 
The reboot after 2 hours again seems to point towards either memory problems or package problems.

---

