---
title: "Using ubuntu to recover RAID0 URGENT HELP PLEASE"
date: 2008-08-13
forum: General Help
---

### Post by Killtodie on 2008-08-13
long story short the boot.ini in winXP got changed on a RAID0 setup and now it wont boot to windows.

I can get Ubuntu on the machine. The raid array is still in one piece. how can I use ubuntu to see the RAID0 array so I can edit back the boot.ini file?


or i can boot of the Xp CD and go to repair console and fixboot, but I dont a floppy drive anywhere near here for the raid drivers... or any floppys

---

### Post by unutbu on 2008-08-13
This page shows how to make your RAID0 visible to Ubuntu:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Killtodie on 2008-08-13
That looks only a guide to install ubuntu onto RAID, I need to access my raid from the Live CD.

---

### Post by unutbu on 2008-08-13
The first step in installing Ubuntu on a RAID0 is to make the RAID0 visible to Ubuntu.

---

### Post by Killtodie on 2008-08-13
> **unutbu said:**
> The first step in installing Ubuntu on a RAID0 is to make the RAID0 visible to Ubuntu.

Right, but that guide looks like it might corrupt my existing raid setup
I just dont wanna risk it unless its 100% safe

---

### Post by unutbu on 2008-08-13
"dmraid -ay activates all software RAID sets discovered."
See [http://www.linuxmanpages.com/man8/dmraid.8.php](http://www.linuxmanpages.com/man8/dmraid.8.php).

I don't think this command will corrupt your existing raid setup.
> 
I just dont wanna risk it unless its 100% safe

I understand your concern. It wouldn't hurt to wait for more knowledgable forum readers to chime in -- I don't know that much about RAID.

---

### Post by Killtodie on 2008-08-13
Thanks. In the meantime im trying BartPE. I was able to find a floppy drive. The recovery console didnt work. :(

---

### Post by Killtodie on 2008-08-13
> **unutbu said:**
> "dmraid -ay activates all software RAID sets discovered."
See [http://www.linuxmanpages.com/man8/dmraid.8.php](http://www.linuxmanpages.com/man8/dmraid.8.php).

I don't think this command will corrupt your existing raid setup.


In order for that command to work, I first have to install the raid program which I fear may corrupt my existing raid.

---

### Post by unutbu on 2008-08-13
If you boot from the LiveCD, the filesystem that you see is in RAM, not on any hard drive. You can install dmraid there and it will not touch your hard disks.

---

### Post by Killtodie on 2008-08-13
I'm not worried where its gonna install, im worried what it might do to it ones it find sit.

still trying BartPE, was loading the wrong raid driver the whole time. its 3114 not 3112

---

### Post by psusi on 2008-08-15
You can use dmraid -ay on the livecd to recognize the raid array, then start up gparted and it should mount the ntfs partition on the raid array, then you can modify your boot.ini file.

---

