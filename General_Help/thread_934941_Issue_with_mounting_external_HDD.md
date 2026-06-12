---
title: "Issue with mounting external HDD"
date: 2008-10-01
forum: General Help
---

### Post by seeds34 on 2008-10-01
Ok I'm running on a dual boot system with Win XP Home on one drive and Ubuntu 8.04 on the other. I recently made the upgrade from 7.10 to 8.04 and after doing so have in counted a few problems and lucky most of them have been fixed (I don't mined problems they're the best way to learn). But one thing I can't get working properly is my external hard drive. For a start it doesn't auto mount second when it is mounted I cant do anything with it as it says I don't have permission.



So what I have done and tried:



When eve I mount I use this command



sudo mount /dev/sda1 /media/FreecomHDD

(I made a new folder for the Hard drive)



I've tried following information from here [http://www.linuxforums.org/forum/linux-newbie/46549-chmod-read-only-mounted-drive.html](http://www.linuxforums.org/forum/linux-newbie/46549-chmod-read-only-mounted-drive.html) but to no luck I still do not have permission to use it (unless I do everything via command line as root, and I would prefer not to)



I hope someone might be able to help, just to note I'm novice to Linux so please don't talk to fast :-)

-Seeds

---

### Post by scouser73 on 2008-10-01
Hi, I also had this problem with my external HDDs, what you need to do it go to Terminal, and type **gksudo nautilus** from here nautilus will appear, then make your way to your hard drive, right click, scroll to properties > permissions. From here you can then change the permissions of the hard drive.

---

### Post by seeds34 on 2008-10-01
Thanks for the help, unfortunately i got this error:

"Sorry, couldn't change the owner of "FreecomHDD": Error setting owner: Operation not permitted"

-Seeds

---

### Post by vanadium on 2008-10-01
An external drive should automount. First thing to check if it doesn't is wether the file system is "healthy". If it is a disk you also use under MS Windows, the easiest for you now is to load Windows and have the file system checked over there.

Then disconnect the drive *correctly* from the computer (= shut down the system completely before removing the drive or use the "Safely remove hardware" icon).

Load up Ubuntu. If the mount point /media/FreecomHDD exists, delete it (use "gksudo nautilus", navigate to /media and delete FreecomHDD if that exists; alternatively and quicker: commandline: "sudo rm /media/FreecomHDD")! Then connect the drive. The mount point should be automatically and correctly recreated when you connect your drive.

---

### Post by seeds34 on 2008-10-01
Vanadium thanks for the help unfortunately again nothing has seemed to happen once I turn the hard drive on. Just to note this all worked before updating to 8.04 and it works in Windows.

Thank you for the countries help.

-Seeds

---

