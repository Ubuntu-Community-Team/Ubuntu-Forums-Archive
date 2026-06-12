---
title: "Restoring home drive has broken tab completion"
date: 2008-07-11
forum: General Help
---

### Post by benpage26 on 2008-07-11
Hello, i have been using rsync to create a mirror of my home drive on a regular basis.  Recently I did a clean install of ubuntu.  I did not move versions.

When i copied all the contents of my old home drive it seems to have messed things up a bit.  for example, none of my hidden folders (.bin etc) appeared.

Now i have manually  moved over .bin and added it to my $PATH tab completion will not work for executables in my .bin folder.

For example a file ~/.bin/backup-home exists, and if i typed in "bac[tab]" it would previously have completed the filename, no longer does this happen.

I'm thinking it is possibly something to do with permissions or owner ship, but i 'chown'ed everything in the bin folder to my username, and i've tried permissions 777 and 755, both of which should make them executable to me right?

Thanks if you can help

---

### Post by ajgreeny on 2008-07-11
Did you restore the old home contents back simply by using the "reverse" icon and then using rsync, or did you copy them back as your post suggests.  If the former, I find it difficult to see why the hidden folders didn't restore.

On my system I have rsync (grsync actually) set up to retain all permissions and ownership.  Do you archive in a compressed manner all the home contents or are the files individually rsynced across, and also, perhaps rather importantly, if the latter, is the partition where the backup is stored formatted as fat32 or ext3.  fat32 will not keep permissions, if I remember correctly, and this may be part of the problem.

---

### Post by benpage26 on 2008-07-13
Hi,

The external drive that I backup onto is a ntfs drive, does that keep permissions?  The files are transfered to the backup medium using rsync from the command line in recursive mode, so each file is transfered over one at a time.  I can browse the files while they are on the external backup drive.  To copy them back i browsed to the file, selected all the files, and pasted them back at the home location on my computer.

---

