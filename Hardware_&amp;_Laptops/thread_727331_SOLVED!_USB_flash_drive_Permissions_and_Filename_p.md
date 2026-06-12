---
title: "SOLVED! USB flash drive Permissions and Filename problems solved."
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by eudemus on 2008-03-17
Flash drive is FAT filesystem, Unison (a totally great files & folders syncing software that is multi-platform, and a total Godsend)  failed on permissions. This was not solved by chown - that command failed too! Once I got it working, I then hit issues because of the different way in which lower-and upper-case filenames are handled by FAT and ext3 (Linux) filesystems.

(1) Some general issues:
- Ubuntu Linux repositories have an old version of Unison which attempts to set permissions even where it is told not to (fixed in the most recent versions, apparently).
- Mounting umask=000 seemed to get the drive mounted in such a way as to allow read and write perms generally, and perhaps with the most recent versions of unison this would be sufficient to solve the permissions problems. What (I think) this option does is tells Linux to ignore permissions on this drive - and that's what you want with a FAT drive like a USB stick, because the FAT filesystem doesn't do permissions.

(2) Fixing permissions:
- uid=1000 seemed to do the trick - this mounts the drive as owned by the user. This might have some downsides but I can live with it. I put this in fstab as well.

(3) Filename issues (short directory and file names that were all in capitals got changed into lower case on the FAT volume):
- shortname=winnt (as an option at mount) seemed to be the key to remedying this.

All in all, my mount command looked like this:
sudo mount /dev/sdb1 /media/datastick -o iocharset=utf8,umask=000,uid=1000,shortname=winnt

You need to put these various options also in /etc/fstab too, so that when the thing is mounted again, it mounts correctly. I just edited the fstab file directly, but you can do this from System Settings in Kubuntu, and (from memory) somewhere in the system menu in Gnome (maybe called "disks and drives" or something like that).

Perhaps some of the above displays my limited knowledge or misunderstandings, but this seemed to work pretty well. (At least so far.) Thanks to Unison usergroup for all the advice and suggestions.

Cheers
Jamie

---

### Post by wieman01 on 2008-03-18
There is another solution posted here:

[http://ubuntuforums.org/showthread.php?t=302412]("http://ubuntuforums.org/showthread.php?t=302412")

---

