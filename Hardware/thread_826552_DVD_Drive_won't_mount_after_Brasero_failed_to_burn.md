---
title: "DVD Drive won't mount after Brasero failed to burn a DVD"
date: 2008-06-12
forum: Hardware
---

### Post by wendallsan on 2008-06-12
Hi all,

My DVD drive is no longer mounting DVD's or CD's since Brasero failed to burn a DVD a few days ago (it has successfully burned disks in the past with Brasero).  Is this a known issue?  Is there some way to get use of my drive back?  I'm running Ubuntu 8.04.  Any help is greatly appreciated.

Update: I've checked my fstab and it looks alright:

fstab:

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I don't see any entry for my DVD drive in /etc/mtab.

If I try to mount the drive using sudo mount /dev/cdrom I get the message 'No media found' even though I have a disk in the drive that worked fine prior to this problem.

Any help?

---

### Post by wendallsan on 2008-06-13
Anyone?  I don't want to have to format my computer just to be able to use my drive again . . .

---

### Post by wendallsan on 2008-06-21
bump.

---

### Post by damphoud on 2008-06-22
Have you tried to competely remove Brasero and restart? I'm not sure if this would work, as I'm not sure what the problem could be, but might be worth a try...

---

### Post by zeronothing on 2008-06-22
I would try a totally different CD or DVD in the drive and see if it works. even try both if you can to see if one works over the other. Next try to unmount the drive even if it lookd unmounted. then try to remount the drive again. then I would do what damphoud said to do. make sure no other application is trying to use the drive like a media player or other burning software. check by using "system monitor" see if any other applications are running. these suggests might sound stupid but its just the way my thought process would go.

---

### Post by wendallsan on 2008-06-22
Hi all, 

Removing Brasero and rebooting still does not allow me to mount anything in the CDROM drive.  No CD's or DVD's will mount (I have tried several different ones).

I don't see any apps in my System Monitor that would be related to using or burning a CDROM.

Trying to unmount the drive ('sudo umount /media/cdrom' or 'sudo umount /media/cdrom0') results in: 

umount: /media/cdrom0 is not mounted (according to mtab)

Looking at dmesg ('dmesg | grep CD-ROM'):

[   29.122476] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-H552D GA01 PQ: 0 ANSI: 5
[   30.283530] Uniform CD-ROM driver Revision: 3.20
[   30.283609] sr 1:0:0:0: Attached scsi CD-ROM sr0
[  712.975833] ISOFS: Unable to identify CD-ROM format.

I think this means that the CDROM device is '/dev/sr0' from the info above (please correct me if I'm wrong).

running the command 'sudo mount /dev/sr0 -t iso9660 /media/cdrom' or 'sudo mount /dev/sr0 -t iso9660 /media/cdrom0' results in:

mount: No media found

Any other ideas?  Thanks for your help.

---

### Post by chrismine on 2008-06-22
The drive is most probably faulty. Have you tried to boot from a UBUNTU Live CD and see if it boots into the desktop?  If so try to mount a different CD from the live session. If nothing works try to borrow a different drive and double check.

Hope it helps.

---

### Post by wendallsan on 2008-06-22
Hmm, you're right, the Ubuntu Live CD I used to install the OS originally doesn't work now.  Maybe this drive is just hosed, which sucks, but at least it's not a Linux problem, I guess.

Any other ideas before I blow $50 on a new drive?

---

### Post by chrismine on 2008-06-22
Unfortunately no other ideas from my side. I had a Samsung DVD burner went bad some time ago.

---

### Post by wendallsan on 2008-06-24
You called it, I dropped a different DVD drive in today and it worked fine, guess my old drive just crapped out on me!  Thanks for all the help and narrowing down the possibilities.

---

