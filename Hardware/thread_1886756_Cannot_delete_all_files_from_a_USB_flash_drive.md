---
title: "Cannot delete all files from a USB flash drive"
date: 2011-11-25
forum: Hardware
---

### Post by alreadytaken4536 on 2011-11-25
I have a flash drive that holds about a gigabyte of information, and I need to fit a gigabyte file onto it. I deleted everything on the drive, but there is some left over hidden stuff that I can't seem to get rid of. If click View -> Show Hidden Files, I get a lovely folder called .Trash-1000. Inside are essentially copies of everything I deleted. Now when I try to delete THESE, I get error messages related to how they are "read-only file systems". So I decide to try terminal.

sudo rm -rf in the directory of the flash drive didn't work, so I don't know what else I can do. Is there a way to just reformat the drive?

---

### Post by BC59 on 2011-11-25
No just empty the trash in your computer and the files will gone.

---

### Post by NewsMan2010 on 2011-11-26
You might try this...
 
I had a similar issue. My 1gb USB was setup with a Ubuntu ISO to boot and install from and it was showing up as write protected. No matter what I did, I could not delete the ISO from the USB in WinXP, Win7 Pro, or Ubuntu 11.10.
 
So after getting a new 16gb USB stick, I decided I'd try to update that 1gb stick from the last version of Ubuntu and to the newest.
 
While going through the procedure to create it, (just look at how to create a bootable USB stick in the instructions for downloading Ubuntu 11.10), you get to a part called "Make Startup Disk."
 
Under "Disk to use" click erase disk.
 
That worked for me to get rid of the write protected ISO file and maybe, hopefully it might work in your situation.
 
Good luck!

---

