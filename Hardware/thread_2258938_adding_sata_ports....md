---
title: "adding sata ports..."
date: 2014-12-31
forum: Hardware
---

### Post by iceman30ad on 2014-12-31
ok i have a few harddrives and my mobo  built in sata ports are all used 
yes all hard drives are 75% + used
adding more hard drives and a blue ray player and a raid card
not looking for redundancy or to stripe just wanting to have my hard drive set up expanded 
current set up
4 sata ports
1 cd/dvd
1 hd / /home  500 gB
1 hd /tvshows 1 TB
1 hd /movies 2 TB
 new set up wanted
4 sata ports on mobo
2 sata ports on raid card
1 cd/dvd on mobo
1 BR on mobo
1 hd / /home 1 TB on mobo
1 esata connecton mobo or raid card ? the 500 wlll connect here aong with about 6 other hard drives intermitantly
1 hd /tvshows 2 TB mobo raid?
1 hd /movies 4 Tb mobo raid?
is what i want to do possible or will i need to make it a raid 0 and hope i keep data

---

### Post by weatherman2 on 2014-12-31
You can certainly add a PCI-E SATA card to add more ports if you wish, if you have a spare slot.  You can find plenty of PCI-E cards on NewEgg and elsewhere.

But that sounds like a lot of hard drives.  Can't you consolidate them?  Your first three current hard drives for example could be consolidated onto a single 4TB drive.

Why do you need to RAID anything?  If you want to use RAID to protect against hard drive failure, keep in mind that RAID mirrors do not protect against file system corruption, accidental erasures, infection by a Windows-connected computer, power surge that destroys all the attached devices...these things have all happened to me or someone I support over the years, so a RAID would have been useless.  You should still be backing up your important data somewhere else, for example to a USB or eSATA hard drive that is normally not plugged in to your computer, to protect it against unintentional problems.

My setup would be:

1 SATA port - SSD drive for the OS
1 SATA port - large hard drive for data
1 SATA port - Blu-Ray drive  (do you need a separate CD/DVD drive?)

External backup devices.  If you want regular backup, have say two large USB 3.0 drives, one always connected, the other always not connected, that get synced to your data daily, then swap them once in a while, so you always have a secure copy offline.

---

### Post by iceman30ad on 2014-12-31
ok the data is easly replaceable, we have all the orignal dvds. We use this as a media server for the house so we are not loosing the dvds and evey now and then i clone a dvd for the kids to watch in the car. does that explain our usage. i am also upgrading the storage adding a 4 tb and removing the 500 gb. the extra hdds i have external contain custom isos for movie sets i burn for our frequent road trips and the dvd no longer burns but reads just fine.

and i do keep backups to 3 diffrent locations in diffrent states we keep a partiton open for backups for each other.

---

