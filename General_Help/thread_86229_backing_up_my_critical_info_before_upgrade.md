---
title: "backing up my critical info before upgrade"
date: 2005-11-04
forum: General Help
---

### Post by Brandon14u2 on 2005-11-04
I was thinking about upgrading.  What files do I need to back up in order to keep my critical information.  Just the /home directory, right?  
Thanks,
Brandon

---

### Post by wrtrdood on 2005-11-04
Good start but I always backup the /etc directory and because I use mysql for some things, /var/lib/mysql (where the database files are kept).  I forgot both of those one time and regretted it dearly...

---

### Post by Kyral on 2005-11-04
Upgrading to....? Breezy?

Yah, /home is where all your user specific settings are stashed. But system-wide settings are stored in /etc mostly.

Don't worry, Dist-Upgrading to Breezy is mostly painless, and anything that breaks won't be on the level that you would need to restore like that

---

### Post by mlomker on 2005-11-04
You might want to save a copy of /etc somewhere, if you've customized your system settings (networking, etc).

---

### Post by Brandon14u2 on 2005-11-04
so after I upgrade, would I simply need to replace the new directories with the old ones or is there something else that's needed to be done?

---

### Post by mlomker on 2005-11-04
[QUOTE=Brandon14u2]so after I upgrade, would I simply need to replace the new directories with the old ones or is there something else that's needed to be done?[/QUOTE]

That would be true of /home.  You wouldn't want to overwrite everything in /etc.

I'd recommend making /home a separate partition when you repartition your drive.  It'll spare you from having to back it up next time.  I use 6 Gig for / and the rest for /home and it works out quite well.

---

### Post by stoic jed on 2005-11-06
When backing up your /home directory, be sure to preserve file permissions. I recently upgraded to Breezy and realized after it was too late that all files and directories were stripped of their original permissions in the process of burning them to CD.

---

### Post by mlomker on 2005-11-06
[QUOTE=stoic jed]When backing up your /home directory, be sure to preserve file permissions.[/QUOTE]

You can [use tar]("http://www.ubuntuforums.org/showpost.php?p=361622&postcount=4") and then burn the file to CD, FTP it somewhere, etc.

---

### Post by bionnaki on 2005-11-07
how would you set the /home directory so that it matches with the rest of the directories? that's what I dont get...meaning, when you click "home" in nautilus, how do you get it to open the designated partition instead of the /home on your limited 6 gig partition?

---

### Post by mlomker on 2005-11-07
>  /home on your limited 6 gig partition?

You just mount it there by putting it into your /etc/fstab.  Normally the mount point is just an empty directory:

```

/dev/hda5       /home           reiserfs defaults        0       2

```

If you do your partitioning in the installer program then it'll create the /etc/fstab file for you, of course.

---

