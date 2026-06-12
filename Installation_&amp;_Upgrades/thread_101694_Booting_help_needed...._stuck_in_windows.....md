---
title: "Booting help needed.... stuck in windows...."
date: 2005-12-10
forum: Installation &amp; Upgrades
---

### Post by niño bomba on 2005-12-10
Hello... i have just installed a breezy badger version of ubuntu. My computer has 2 hard disks, and the installation process seemed to go fine. It detected my previous windows install (which i don't want to lose just yet) and asked me whether or not i wanted to set grub in the booting disk i responded yes and the process ended by saying it had been succesful and the computer needed to be restarted. It also said that it would ask me which system i wanted to boot upon restart.
The problem is everytime i restart, it goes back into my old windows xp pro... no questions asked no options allowed.
Does anybody know how can i get GRUB (who i think is responsible of giving me the options) to boot before windows takes over?
How can i make my computer start in ubuntu, and leave his windows addiction aside for a while?
Lots of thanks to anyone out there willing to help.
:confused:

---

### Post by taurus on 2005-12-10
Did you have GRUB installed on MBR--Master Boot Record???

---

### Post by aysiu on 2005-12-10
[QUOTE=niño bomba]It detected my previous windows install (which i don't want to lose just yet) and asked me whether or not i wanted to set grub in the booting disk i responded yes and the process ended by saying it had been succesful and the computer needed to be restarted.[/quote] So you got this dialogue (see attached image) and answered "yes"? If so, that should have done the trick (i.e., you did what you were supposed to).

> 
The problem is everytime i restart, it goes back into my old windows xp pro... no questions asked no options allowed. I wonder if it has something to do with them being on separate drives...? I have a dual boot, but it's one hard disk separated into different partitions.

---

### Post by niño bomba on 2005-12-10
Yes i got that dialog. And I expected the trick to be done.
Should I repartition the windows disk and install ubuntu there? 
Is there any problem with a single disk having three partitions then?
Because what I really wanted to do was leave my second hard disk for linux only.... so to be neat and organized and even label my disks "linux disk" or "windows disk". 
Thanks for the attention.

---

### Post by hod139 on 2005-12-10
There shouldn't be a problem with having windows on one physical hard drive, and ubuntu on another.  Just out of curiosity, did you install, reinstall, or repair windows after installing ubuntu?  Windows will overwrite the master boot record without asking/caring if another boot loader is there.  You can try reinstalling just grub, or all of ubuntu and see if this problem goes away.

---

### Post by aysiu on 2005-12-10
[QUOTE=niño bomba]Yes i got that dialog. And I expected the trick to be done.
Should I repartition the windows disk and install ubuntu there?[/quote] You can. The obvious advantage is that I have experienced that to be a working configuration. The only thing you have to keep in mind is that repartitioning generally doesn't cause any problems, but you should **always** back up your data. Otherwise, you're driving a motorcycle without a helmet.

> 
Is there any problem with a single disk having three partitions then? No. I have three partitions (and a swap partition... so four, sort of). I used to have five.

> 
Because what I really wanted to do was leave my second hard disk for linux only.... so to be neat and organized and even label my disks "linux disk" or "windows disk". 
Thanks for the attention. I would advise you divvy it up this way:

Hard Drive 1 (first partition): Windows
Hard Drive 1 (second partition): Ubuntu and swap
Hard Drive 2 (entire partition): FAT32 format to share files between the two operating systems.

---

### Post by niño bomba on 2005-12-10
No, i didn&#180;t repair windows at all. Unless perhaps a program did it and i didn't notice. I do have installed Norton GoBack.... do you think this is the one messing up the rest?

---

### Post by hod139 on 2005-12-10
I don't think Norton would touch the MBR without at least asking first.  I would try follow the [howto: Restore Grub]("http://ubuntuforums.org/showthread.php?t=76652") post, and then if it still doesn't work keep asking questions here.

---

### Post by taurus on 2005-12-10
Just want to also point out that Ubuntu doesn't have to be on the first HD because I don't have any problem booting it from my second HD at all!!!  Are you sure you answer "Yes" to that question instead of "No?"

---

