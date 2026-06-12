---
title: "want to revert to xp, but want to keep some files"
date: 2008-07-14
forum: General Help
---

### Post by ycomp on 2008-07-14
Hi, my problem is this...

I am relative ubuntu newbie...

I want to install XP back on my laptop which is currently ubuntu...

laptop has 1 big partition i think... well anyhow, the bulk of space would be 1 partition.

problem is that I have about 25 gigs of videos that I don't want to lose. I tried plugging in my usb ntfs drive but that didn't work. And I don't have enough blank dvds to copy the files.

Can I make some kind of new partition and move the file there? And then install XP without harming this partition?

if i make it a linux partition, how can i read it in windows xp?

or is there a way to make it an ntfs or fat partition?

---

### Post by cmnorton on 2008-07-14
You cannot read a linux partition in XP.

Something is awry if you could not get a usb drive to work, ntfs or not.

Without auto-mounting, my usb drive sits on /dev/sdb1. If I mount through the icon on my screen, the volume name KITS is used as the mount point. 

(Assuming I am at a command line -- X-term -- while issuing these commands.)

So after using the icon's menu to mount, df results in 

/dev/sdb1              1999004   1771196    227808  89% /media/KITS

Even if you don't have an icon on your screen, you could try

sudo mkdir /media/usb_mnt

# usb_mnt can be any name that makes sense to you

sudo mount /dev/sdb1 /media/usb_mnt

Copy stuff off, and then

sudo umount /media_usb_mnt

If this does not work, try another flash drive.

---

### Post by ycomp on 2008-07-14
thanks for the help... I think i figured something out though...

couldn't find partion magic cd, so downloaded gparted... it is ok but very slow... guess I shoulda went with the knoppix

anyhow, shrunk ext3 partition... tried to make a fat32... fat32 doesn't work with ubunutu... at least when I tried to mount it and then copy my files there, I had some error message.

now I deleted that fat32 32gb partition and replaced it with ext3.

then i will install xp and use one of the linux partition explorer programs for xp. probably this explore2fs

I think it should work

---

### Post by ycomp on 2008-07-14
hmmm ... no dice... can't mount an ext3 partition in ubuntu either. Same error message. 
"Error while copying. There was an error getting information about 31.9gb media.volume. The specified location is not supported."

oh... I forgot to format it with gparted... (the fat32 I had before, I did format). How do I format an ext3 partition in ubuntu?

---

### Post by jonian_g on 2008-07-14
> I tried plugging in my usb ntfs drive but that didn't work.

What you mean it didn't work? You plug it and nothing hapens or you can't copy anything inside the usb drive?

> Can I make some kind of new partition and move the file there? And then install XP without harming this partition?

Yes you can.

> if i make it a linux partition, how can i read it in windows xp?

You don't have to make a linux partition (ext3, ext2 etc.), you can make a windows partition (ntfs, fat32, fat16).

The quickest way to do it is with the external drive but you have to tell what you mean it didn't work.

---

### Post by ycomp on 2008-07-14
1) now I made an ext2 32gb partition with gparted... I try to copy the video files from the desktop to it and it says "permission denied"

2) if I plug in external NTFS usb drive it says "Cannot mount volume". Unable to mount the volume 'New Volume'. 

[mntent]: line 10 in /etc/fstab is bad
mount: can't find /media/New in etc/fstab or /etc/mtab

---

### Post by ycomp on 2008-07-14
cool! i tried norton's suggestion if you can't see icon... then I actually found it gave me a useful help message! apparently you must safely remove usb harddrives from windows computers first... so I plugged it back to vista, safely removed it and now it can be mounted (although not automatically... that will still give the error)

---

### Post by jonian_g on 2008-07-14
Ok... Plug your external drive. Go to add/remove and install "Storage Device Manager".
Once installed go to System>Admin>Storage Device Manager.  When the program starts chose on the left column your external drive (sdb, sdf don't know which really is, you can see it in gparted). On the right give a name to your disk "ex. external". Then click the "assistant" button and on the first tab check "Owner user of the filesystem" and next to "uid=" put your username. Press ok and then the "mount" button. Your external drive will be mounted and you will see an icon on your desktop and you will have write permissions. You can do the same thing with the partition you created on your internal drive.

---

### Post by ycomp on 2008-07-14
thanks for the help

---

