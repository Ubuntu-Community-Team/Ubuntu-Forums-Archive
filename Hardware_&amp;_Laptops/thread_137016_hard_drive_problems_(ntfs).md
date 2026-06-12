---
title: "hard drive problems (ntfs)"
date: 2006-02-27
forum: Hardware &amp; Laptops
---

### Post by el_ricardo on 2006-02-27
hi, just got ubuntu running just the way i like it, so i thought i'd get round to adding a hard drive from my old computer with all my music on it, this hard drive ofcourse being in ntfs because my old computer was running windows. the problem is that it just doesn't seem to mount, linux knows it's there, if i go in system>administration>disks, but it won't let me enable the partition. i've used various other programs to try and fix the problem, i figured a defrag would get it working, but i can't seem to find any software that wil do this, i tried it with ntfsprogs with no success, the only other option is repairing it from windows with chkdisk, and then defragging, is there any other options before i resign myself to taking the time to move it to another computer? (because i really can't be arsed right now)

do you think i would be able to access the drive through winefile? seen as though this drive used to work in windows no problem...

my drive configuration is:

linux partition- /dev/sda1
ntfs partition- /dev/hdb1    <-- yes, this is the only partition other than the MBR
dvd- /dev/hda

switching it round so the ntfs drive is the master and the dvd drive is the slave screws it up for some reason (this configuration seems to make more sense to me)

---

### Post by newuser111 on 2006-02-27
sudo mkdir /media/windows
sudo mount /dev/hdb1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

add the following to your /etc/fstab to get the ntfs partition to mount automatically on ever boot

/dev/hdb1       /media/windows  ntfs    nls=utf8,umask=0222 0       0

---

### Post by el_ricardo on 2006-02-27
cheers, thats got it working, and thanks for the fast response too!

---

