---
title: "How to replace volume name with mount point name on desktop and gnome gui?"
date: 2008-10-05
forum: General Help
---

### Post by ubunny on 2008-10-05
I just upgraded to Hardy from Gutsy and all is well.  (Waiting was a good idea)

However my external drives where it previously would be indicated on the desktop as their respective mount point names ie: /media/disk , /media/disk-1, /media/disk-2,  and /media/disk-3 are now using under Hardy the volume label names of "20GB Media" over and over (not my name, some default) for each drive.

It's difficult to select the correct drive in other programs without specifying the correct /media/disk mount point name.  

How do I get Hardy to stop using the Volume names and instead use the mount point names instead like Gutsy such that it will report the mount point name in the gnome gui and desktop?

Thanks

---

### Post by ubunny on 2008-10-06
uh oh... on the desktop i went to properties, clicked Volume and put /media/diskN into the boxes there, and now I can't mount any external drive.

how to reset the drive properties to blank so that it doesn't load these settings i added from the volume tab?

---

### Post by ubunny on 2008-10-06
I found the configuration files in .gconf and gconfd deleted them but it didn't recover the disks for mounting.  I think I forgot to check the Places menu, they may have been there...

instead of doing that though, I did rm -rf .gnome .gnome2 .gconf .gconfd .metacity to rebuild desktop from scratch and at least it loads the drives.  

Now just have to resolve the original issue of mounting the drives via their media name not their volume names.  Also now after this rebuild, they don't automatically load to the desktop.

Thanks to self so far.  Notes here for anyone in similar situations.

any ideas on changing the default display titles?

---

### Post by Reardon on 2009-01-24
Same issue here: has this been resolved elsewhere?  Have searched extensively for a solution.

---

### Post by mc4man on 2009-01-24
> Same issue here: has this been resolved elsewhere? Have searched extensively for a solution. 

If that's how to change the default mounting behavior, ie. mounting to /media/'volume label', never really looked at, may or may not be possible.

Far better to give your usb drives distinctive labels, see here for how to:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Then the display name will be whatever you labeled the drive (volume)

If it's you can't mount due to messing with mount option in the properties, easily fixed, no need to 'rebuild' desktop as above

---

### Post by Blibit42 on 2009-01-24
I have the same problem with 11 drives formatted reiserfs that all say "1000.2 GB Media" and I have 11 million files on them.

If my desktop gets rearranged, it is like playing musical chairs (or hide and seek) to find the drive I want because they come up in some mystical order known only to the xubuntu gods... (yes, I can go open the media directory and find them by their mount points, but that is a pain).


If someone knows if the USB method listed by mc4man will work without losing data, please let me know, or if you know another way to change the default names to show the REAL mount points without rebuilding the partitions or editing the partition label entry (which may force me to recopy all 11 million files), I would be very grateful! (it was a big getting all that data onto the disks).

Thanks,
Blibit42
Quad Core Intel Q6600 on Intel motherboard,
8Gb PC6400 RAM - 80Gb WD SATA System drive
11 1TB WD "Green" drives on Sil3114 PCIe RAID controllers
And if you are wondering, these drives run cool as a cucumber 
and use about 40% less power (measured it myself), but they are 
about 7% slower (on average) than their full power 32 MB cache WD brothers.
-- I am trying to get my electric bill down below by mortgage payment :)

---

### Post by Yashiro on 2009-01-24
- Label the drives 
- Install the filesystem tools (e2fsprogs,ntfsprogs,mlabel,whatever) the and use gparted to label them.
- Put the drives into your fstab with specified mount points.
 use uuids and assign specific mount points. (best)

This is all available by searching here or google.

If you use the gui properties to change mount points, and you enter bad data.. Open **gconf-editor** and delete the keys beneath **/system/storage/volumes**.

---

### Post by Blibit42 on 2009-01-24
"If someone knows if the USB method listed by mc4man will work without losing data, please let me know..."

Unmounted it, used reiserfstune --label NAME Device (as recommended) and added the label. It added the label, but it still  does NOT show the label from the reiserfs volume on the desktop. I thought it would work, too.  So much for thinking. 

Well, it is not THAT big of a deal. It is just an ankle biter as far as problems go.  But if someone finds out, don't hesitate to let us know!
Thanks,
Blibit42

---

### Post by Blibit42 on 2009-01-24
Thanks Yashiro!

I should have refreshed the page before posting again and I would have seen you reply. Just changing the labels did not work, but I will try it use the uuid in fstab and see what happens.

I have been searching Google, the ubuntu forums and elsewhere, but maybe I did not find the answers because I was not asking the right questions.

---

### Post by Blibit42 on 2009-01-24
After successfully adding the volume Label TB11 with reiserfstune, I have tried all of the following in fstab along with the mount command to go with them:

```
/dev/sdl1 /media/TB11 reiserfs user,suid,dev,users,exec              0 0
```

```
UUID=165000f8-9827-4324-bd1b-876dd741e2e0  /media/TB11     reiserfs     user,suid,dev,users,exec               0  0  
```

```
LABEL=TB11 /media/TB11     reiserfs     user,suid,dev,users,exec               0  0
```

I even got desperate and tried nonsensical stuff like this:

```
/dev/TB11 /media/TB11  reiserfs  user,suid,dev,users,exec               0  0

```
```
TB11 /media/TB11     reiserfs     user,suid,dev,users,exec               0  0

```

The mount point is the directory /media/TB11 which is also shared on the SMB network (which works fine).

I have tried mounting manually as user, then as root, and on reboot, and via storage manager, and it always comes up as
**1000.2 GB Media** on the desktop no matter what I do. The label is correctly on the volume (The label name shows up properly in gparted and elsewhere).

For additional info, I need users to be able to mount and unmount the volume (4 or 5 people work on the files that are on these volumes) and sometimes they also need to pull the whole disk and do volume copies on a SATA hardware disk copier). I want (need) reiserfs for its ability to handle millions and millions of small files rapidly without wasting any space (which is does really well), or I would try one of the other file systems.

***Any ideas what I am doing wrong?*** Could it be an issue with reiserfs and 8.04 LTS?

One other note is that even though the man page says I should be able to mount by volume label, it does not work with these reiserfs volumes. The GUI is XFCE so no gconf-editor with it (which I really like - small, fast, light weight). 

Thanks,
Blibit42

---

### Post by Yashiro on 2009-01-24
> and it always comes up as
1000.2 GB Media on the desktop no matter what I do. The label is correctly on the volume (The label name shows up properly in gparted and elsewhere).
So what is handling these desktop icons?

---

### Post by mc4man on 2009-01-24
I just tried with a usb drive, formatted reiserfs, gave it a label with reiserfstune. When remounted came up drive size instead of volume label for display name.
Physically removing and then reinserting came up volume label for display name

Also did an internal partition, in this case had to **reboot** to get the display name to change.

The fstab stuff is irrelevant, volumes are displayed by volume label, if none is present than volume size is displayed. Entries in fstab will not change that.

---

### Post by Yashiro on 2009-01-24
It's not totally irrelevant if the labels can be made to correspond with their mount points, which was asked originally.

---

### Post by mc4man on 2009-01-24
The display name is based on the volume label, if there is no fstab entry then the mount point will be /media/<volume Label>.

If there is a fstab entry the display name will still be the volume label irregardless of the mount point set in fstab.

So you'd turn that statement around
"if the labels can be made to correspond with their mount points"
to
if the mount points can be made to correspond to their labels, which still has no effect on the display name.

The only effect here from fstab entries is to mount at boot to a particular mount point with particular mount options.

---

