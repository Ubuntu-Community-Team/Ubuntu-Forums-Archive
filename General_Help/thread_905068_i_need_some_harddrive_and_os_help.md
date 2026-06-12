---
title: "i need some harddrive and os help"
date: 2008-08-29
forum: General Help
---

### Post by tercelkisor on 2008-08-29
k..  i hae 3 harddrives... 2 40's on the 1st ide and a 20 slave on the 2nd ide.

k what i wanna do is delete everything off all the harddrives and put xp on one 40 and ubuntu on the other 40(i have both disks)

how could i do this and how should i set up my drives in like wire order and jumper position... i want the 20 to be a slave for xp(extra storage)

thanks

also what are some forseen problems with this type of thing?

---

### Post by Shazaam on 2008-08-30
Your motherboard should have two IDE ports labeled IDE1 and IDE2. Something like this...

IDE 1 Data cable.
1. Primary IDE drive (40gig) w/jumper set to Master on END of cable.
2. Slave IDE drive (40 gig) w/jumper set to Slave on other plug.

IDE 2 Data cable
1. CD/DVD-rom drive w/jumper set to Master on END of cable.
2. Slave IDE drive (20gig) w/jumper set to Slave on other plug.
Windows will go on the Primary Master 40gig drive FIRST.
Ubuntu/linux doesn't care, you can put it anywhere.

---

### Post by retrovertigo on 2008-08-30
To add to what Shazaam said, it would be a good idea to install XP first as Windows will overwrite your MBR.  You can always use the LiveCD to boot back into Ubuntu and reinstall GRUB, but it's less of a hassle to just install Windows first.

---

### Post by tercelkisor on 2008-08-30
thanks.  im going to try it out tomorrow.  appreciate it.

---

### Post by tercelkisor on 2008-08-30
wait i forgot something.

how would i go about removing everything from the hard drive?

i cant format in xp cause both 40's have applications being used on them(i think part of an update was installed on the extra one) and the 20 isnt in my computer...

how would i format without using xp.

also the xp disk i guess is supposed to do that but the last 2 times i reinstalled xp it still had all the crap from before.

im thinking that i find a way to format one drive and install the new xp on that and format the others after xp installation but idk how well that would work.

---

### Post by Cato2 on 2008-08-30
To format all the drives you need, try using the Ubuntu Desktop (Live) CD - make sure your BIOS is set to boot from the CD, then reboot your PC.  Ubuntu then is independent of the hard drives.

**Important tip:** If you have any data at all on these drives, back it up before you start.  Also, if one drive is not going to be reformatted, physically disconnect it (remove IDE cable) before you start.  This helps avoid losing data which is VERY easy - Ubuntu/Linux can rename disks from sda to sdb which is quite confusing, particularly when you go from normal booting to the live CD.

To identify the disks after reboot, try ```
sfdisk -l -uM
``` which uses units of Megabytes - these should correspond to sizes of your disk partitions.  Another good tip is to create a text file using the Nautilus file manager on each drive that says what it is, e.g. "windows-drive.txt", "linux-drive.txt", etc - that way you can very quickly check which is which after you reboot.

---

### Post by tercelkisor on 2008-08-30
k how would i format them tho... what would i do while booted on the live cd?

---

### Post by tercelkisor on 2008-08-30
k i formatted all hard drives in gparted. they are all empty now.

but when i put my xp cd i get an error: pxe-e61 media test failure check cable

and pxe-m0f exiting intel boot agent.


idk what to do.. the ubuntu cd loads...  but xp aint wrkin

---

### Post by Cato2 on 2008-08-31
No idea on the XP question - suggest you google for those error messages and ask on a Windows forum.  Make sure your BIOS is booting direct to the Windows disk, and try removing the Linux disk temporarily.

---

