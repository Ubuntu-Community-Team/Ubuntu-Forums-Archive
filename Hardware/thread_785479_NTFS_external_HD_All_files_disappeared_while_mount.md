---
title: "NTFS external HD: All files disappeared while mounted in ubuntu..."
date: 2008-05-07
forum: Hardware
---

### Post by chochem on 2008-05-07
The upshot: I have an external WD 500 Gb drive which is NTFS formatted (orig. FAT32, formatted on receipt to NTFS). During a recent ubuntu session with a high number of manual (sudo mount) mounts and dismounts, I discovered to my horror that all files had gone. A few empty  directories still remain - about half the toplevel ones and a lot of sublevel ones. 

The background: The drive had been performing somewhat erratically after a recent hardy install. Since I suspected that maybe NTFS was not the  best choice of FS for a (now) primarily linux system, my first brillant idea was to run chkdsk on it, reduce the size of the NTFS partition to half of the available space, make an EXT3 partition on the other half and copy the files, delete the old partition, extend the new. I got to the point of running CHKDSK (found and fixed some errors) and reducing the size of the NTFS partition (in the windows app Acronis Disk Director, since gparted wasn't willing). I then booted back into Ubuntu and created the EXT3 partition but I noticed that mounting and entering directories on the NTFS partition was still painfully slow and so, I thought that maybe it was HAL not the disk that was being troublesome (in Gutsy it eventually managed to **** up mounting my MP3-player). So I abandoned the first plan in favour of a re-install without Hal (my alternative was editing /etc/sudoers and allowing the users group to mount and umount without password and then do a basic 'toggle mount' script and assign it a key combo). And well, this worked perfectly; the drive mounted easily and stably. Right up to the point where my files were gone, that is... 

The questions: a) does anybody have a guess as to what happened? my only assumption is that the MFS must have been corrupted since there is a neutron bomb quality to it: hollow directories still standing with no files in them. b) does anything I've detailed qualify as certifiably insane and making this a bound-to-happen-scenario? c) any ideas as to what to do next? Foremost, testdisk, ntfsundelete all seem bo options. Any recommendations?

---

### Post by chochem on 2008-05-20
anybody?

(bump)

---

### Post by chochem on 2008-05-21
Oh well, I'm giving up on this... No programs, neither windows, nor linux seem to be able to call my files back from the grave. And my fancy script just erased all my mp3 player's files too... It may be foolhardy but I really did like the way it handled things, just not the mass deletion... so I tried adding a few options to it, mainly the -o sync option, the lack of which is my main stab at a culprit (i.e. I may have unplugged the drive while some vital data hadn't been written because of the async option being default). Here's my new line - I'd really appreciate comments before I entrust it with any more data:

sudo mount -o uid="$userid" -o gid="$groupid" -o rw -o sync -o dirsync -o noatime -o nodiratime -L $label "$mountpoint"

---

### Post by patrick102 on 2008-10-05
hi

understand your frustration. I had this problem recently and found a fix for my files disappearing in rhythmbox - at least they just reappeared when i applied this. 

it is supposed to be something to do with the ntfs file system.

sudo apt-get install ntfs-config

then run the app in system tools menu under applications.

enable write support and check all the options are as they should be. 

its basically scanning for the files but because it is not correctly configured, they disappear from the database as it cannot find them.

i am a total noob to linux but this worked for me. my explanation may not be technically correct but other input would be appreciated. i found this solution on google...

---

