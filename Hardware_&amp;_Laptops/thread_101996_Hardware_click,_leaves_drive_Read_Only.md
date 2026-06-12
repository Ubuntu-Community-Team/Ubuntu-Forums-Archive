---
title: "Hardware click, leaves drive Read Only"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by chz on 2005-12-11
a few weeks ago after coming back after a long weekend, i noticed my hoary desktop to be frozen. didnt think anything of it, rebooted, and then couldnt get on...it continued to say some fsck error. so i got in to the terminal and just ran fsck without any parameters and it did the check listed a number of errors and a question to fix after each one. was able to go through the entire check of the drive and away i went back on to the desktop. 

all smooth, did the normal, watched tvtime, played my music through beep, browsed the net, whatever. up until about 20 minutes ago i went through nautilus to check out some files, and it just hung there. tried to go to the epiphany, noticed it hung there as well. Ctrl-Alt-Backspace to get out of desktop to see if maybe X was acting up, only to have the entire system hang. ok rebooted. let it load through, then noticed my harddrive make a click sound and then it sounded like it was respinning the drive, but it loaded hoary fine, logged in, noticed no errors. did a couple things to test it out. hangs again. restarted again, here the click and respin again. this time nautilus opens up, i browse, try to open a file, and it attempts to open the application, but the load dialog disappears after some time. 

try random programs, 
tvtime...opens, 
beep...opens, 
streamtuner....Error, "cannot write to drive, read only". 
When i close streamtuner...
Error, "cannot save settings, drive read only"...
Error, "unable to create a temporary file: read only file system"....
Error, "unable to save cache, read-only file system"...
and then a few more errors

im not super linux savvy, but i always see ppl trying out "dmesg" and thought maybe it might put out some messages with hardware problems. try to open up a terminal window...no luck. so i decide to Ctrl-Alt-F1...boom...mad error messages popping out, repeating over and over again....

"EXT3-fs error (device sda1) in start_transaction: Readonly filesystem"

ok so now i'm stuck with this...rebooted a couple times, with the same issue over and over again. don't know what more to do. any suggestions?

if you need hardware specs, AMD sempron 2400+, 250gb SATA hd, 512mb RAM, Soyo Dragon Mobo with a running version of Hoary Ubuntu from the day it was released.

---

### Post by hda on 2005-12-11
Looks like a hardware error.
In that case I would suggest booting from a rescue CD and do a badblocks scan for the entire disk. Running
```
badblocks /dev/sda
```
will check the disks for errors in read-only mode.

---

### Post by chz on 2005-12-13
ok, sorry for the delayed reply. i left the machine off for a little while, (a day or so), and then turned it on with it trying to boot into the machine. It tried to run its 30 day check for errors, and found errors on the disk and recommended me to run fsck, and then through me into the root command rite away. ran it on all the drives on the machine, and again it found errors within the drives, corrected the "inodes" or whatever (cant remember the exact error message, but they were pretty much the same). everything apparently got corrected with no problems, and then it mentioned to reboot.....and so i did. rebooted and now the drive and OS work fine.
rite now im curious as to if there is a way to change the 30 boot time checks into "every boot time check"...i run this as a server, so i don't want to have to reboot the machine 30 times to be able to run the check. anybody know how to do this?

---

### Post by psusi on 2005-12-13
You should take hda's advice and run badblocks.  By the sound of it the drive is crashing.  If so, you should start making regular backups of your important data if you don't already, and plan on buying a new drive in the near future, unless it is still under warranty.

---

