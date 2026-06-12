---
title: "[SOLVED] Mount NTSF partition permanently"
date: 2008-10-26
forum: General Help
---

### Post by drazabyss on 2008-10-26
One of these days I might get the hand of this...

Ok, all of the threads I ran into seem a little dated and I'm afraid my knowledge is not up to the task of substituting old data with up to date...

All that I am trying to do is mount an area of my NTFS windows partition permanently.  It works easily enough for me just to click on the partition from Nautilus and it auto mounts and shows up on my desktop.  However I sometimes forget to do this first thing and problems will occur (like Amarok trying to scan one of the watch dirs on that mount and then forcing its self to rescan once it is mounted, etc.).  Since I just went through mounting my windows network, I figured this would be a piece of cake.  But I cannot seem to find the walk through that I need.  Any help will be greatly appreciated!

----------------
Now playing: [The Decemberists - The Engine Driver](http://www.foxytunes.com/artist/the+decemberists/track/the+engine+driver)

---

### Post by ghost_ryder35 on 2008-10-26
add it to 
/etc/fstab

this walkthrough is decent (although its not really a walkthrough)
[http://www.linuxforums.org/forum/suse-linux-help/112670-ntfs-3g-fstab-suse10-3-a.html](http://www.linuxforums.org/forum/suse-linux-help/112670-ntfs-3g-fstab-suse10-3-a.html)
perhaps someone else has a walk through

---

### Post by drs305 on 2008-10-26
It hasn't changed recently, so any fairly new posts should do the job - but here's another one:

[COLOR="Sienna"]Note:[/COLOR] You can install 'ntfs-config' and then run Applicaitons, System Tools, NTFS Configuration Tool to set up fstab automatically.

Type in **bold** indicate you must change to your specifics.

Make the desired mountpoints for the partitions (if they don't exist). Change **mount1** to your desired mountpoint name:
```
sudo mkdir /media/**mount1**
```

Make yourself the owner of the mountpoints if desired. This will make you the owner of the mountpoint/folder in /media, although for NTFS partitions the file permissions are set at mounting and cannot be changed:
```
sudo chown **username:username** /media/**mount1**
```

Make a backup of fstab and open for editing:
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Add these lines, where sd**XX** is the partition you want mounted at boot (change to your specific device). The 'uid' will set ownership to the user whose id is 1000 (normally the first user of the system). The umask sets permissions of 755 - rwx for owner, rx for group and others. If this is a removable drive I would highly recommend mounting with either a UUID or label. To get the UUID, run "sudo blkid". If you want to use the device designation, substitute the first entry with /dev/sd**XX** :

```
# /dev/sd**XX**
UUID=**XXX** /media/**mount1** ntfs defaults,umask=022,uid=1000 0 0

```

---

### Post by drazabyss on 2008-10-26
> **drs305 said:**
> It hasn't changed recently, so any fairly new posts should do the job - but here another one:

[COLOR="Sienna"]Note:[/COLOR] You can install 'ntfs-config' and then run Applicaitons, System Tools, NTFS Configuration Tool to set up fstab automatically.

Type in **bold** indicate you must change to your specifics.

Make the desired mountpoints for the partitions (if they don't exist). Change **mount1** to your desired mountpoint name:
```
sudo mkdir /media/**mount1**
```

Make yourself the owner of the mountpoints if desired. This will make you the owner of the mountpoint/folder in /media, although for NTFS partitions the file permissions are set at mounting and cannot be changed:
```
sudo chown **username:username** /media/[B]mount1
```

Make a backup of fstab and open for editing:
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Add these lines, where sd**XX** is the partition you want mounted at boot (change to your specific device). The 'uid' will set ownership to the user whose id is 1000 (normally the first user of the system). The umask sets permissions of 755 - rwx for owner, rx for group and others. If this is a removable drive I would highly recommend mounting with either a UUID or label. To get the UUID, run "sudo blkid". If you want to use the device designation, substitute the first entry with /dev/sd**XX** :

```
# /dev/sd**XX**
UUID=**XXX** /media/**mount1** ntfs defaults,user,umask=022,uid=1000 0 0

```
Perfect.  Thank you.

---

### Post by drs305 on 2008-10-26
Just as a note, here is how the NTFS configuration tool builds the fstab entry. I do not believe the 'ntfs-3g' designation is required any longer, but it wouldn't hurt:

```
/dev/sdb9 /media/mount1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

---

