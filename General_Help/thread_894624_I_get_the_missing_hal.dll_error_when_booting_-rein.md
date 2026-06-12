---
title: "I get the missing hal.dll error when booting -reinstall or repair and save work??"
date: 2008-08-19
forum: General Help
---

### Post by MeTylerDurden on 2008-08-19
I have tried alot of fixes for the hal.dll file and nothing has worked almost leading me to believe thats not the problem.  I can boot windows xp
just not Ubuntu which is installed inside windows with Wubi.   

What have I done!

---

### Post by MeTylerDurden on 2008-08-19
Will a reinstall lose my work in Ubuntu. How can I save my stuff and do a reinstall.  Can I repair??    sorry about all the questions!

---

### Post by MeTylerDurden on 2008-08-19
I think I tossed some of the partition files that do the boot for Ubuntu, quite possibly in the windows-temp     anyhoo I will check this thread later as I have to work..

---

### Post by robelliott2125 on 2008-08-19
Well, i'm no linux expert, however I feel hall.dll is part of Windows, not Linux.

I'm surprised your Windows loads, since each time hall goes missing (mostly after a "restore" through Windows) I've had to replace the file.

I'd recommend checking what file is missing, and for what OS.

---

### Post by MeTylerDurden on 2008-08-19
I think what is missing is what Linux needs to boot which would be loaded in windows when wubi installed .. thats what i figure

---

### Post by MeTylerDurden on 2008-08-19
I see the hal.dll file in the windows-system32   I am thinking a new wubi install would fix the problem, but don't know how that effect my old install.   Should i be a man and handle my own business and just take the risk of reinstalling and possibly losing everything (there is risk in everything)

---

### Post by minhmeoke on 2008-08-19
You can back up your data with explore2fs [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs) .

---

### Post by echobrain on 2008-08-23
Log into windows ..goto that folder where wubi installed ubuntu..open it..goto the folder "WINBOOT"....there you'll see two files named "wubildr" and "wubildr.mbr"..copy them and paste them into your windows folder..restart your system..and yur ubuntu will run like nothing ever  happened!!!

Trust me..i've had this thing many times!!!!

---

