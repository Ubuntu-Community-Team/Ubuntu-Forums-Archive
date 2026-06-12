---
title: "[SOLVED] Problem deleting files with Nautilus"
date: 2008-08-01
forum: General Help
---

### Post by k0tt0n on 2008-08-01
i'm having trouble with nautilus. i have a program called VirtualBox that i wish to remove completely and reinstall from scratch. i remove it through add remove programs or synaptic but it leaves files that i wish to delete manually. when i open nautilus and do a search for VirtualBox it shows me several files but i am unable to delete them there. so in the terminal i run "gksudo nautilus". now nautilus will open, but when i try a search then it either greys out and doesn't respond or if i try again it may not open at all. other times when i close it, it closes, but something is still going on in the background that hogs all the memory and i can't do anything. is there something wrong with the way i run nautilus when i run the "gksudo nautilus" command? is there some other way to delete all the remaining virtualbox files.
thanks

---

### Post by vanadium on 2008-08-01
There are indeed issues with nautilus when started with root privileges: it will frequently hang. Perhaps it would run correctly if a root account is set up: as you know, Ubuntu does not set up a root account. Alternatively, use the command prompt. For these people who have been familiar with the venerable "Norton Commander", Midnight Commander is a perfect console based clone, and allows for some lightning fast interactive file management without the need to type commands (even the mouse works!). I am sure this will work flawlessly with sudo permissions as well, but make sure that you close it as soon  as you are done doing the administrative work.

To install Midnight Commander:

sudo apt-get install mc

To run it

mc

---

### Post by k0tt0n on 2008-08-01
ok got mc. searched for virtualbox on the entire file system and it came up with nothing

---

### Post by k0tt0n on 2008-08-01
ok. i manually deleted the files using th sudo rm command.

---

