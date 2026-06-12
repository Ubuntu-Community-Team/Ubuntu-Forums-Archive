---
title: "permissions on dvd drive..."
date: 2005-11-07
forum: General Help
---

### Post by bionnaki on 2005-11-07
hello. I have several gigs of photos, ogg/flac/mp3, and movies backed up on dvd-r. when the disks are mount and I attempt to copy the directory/files into my home folder, I notice the permissions on the directores/files are all set at 555 - I am the file owner.

Is this normal? I do not recall having to modify permissions when copying files from dvd/cdrom.

how can I modify the permissions of all directory/files at once? doing the individually would take several hours.

thanks for your help.

---

### Post by bionnaki on 2005-11-07
I also notice that my external harddrive is set at 555 and owner: root - I have never had this problem before. This is a clean installation of breezy and my previous installations did not do this - I could read/write on the external harddrive and I could copy files from cdrom without having to change their permissions.

very odd.

any ideas on whats going on?

---

### Post by bionnaki on 2005-11-07
the files of every cd I put into the drive has these permissions...even older cds from my windows days. I cannot figure out why these permissions are set this way.

[[IMG]http://img118.imageshack.us/img118/3992/lock6li.th.jpg[/IMG]](http://img118.imageshack.us/my.php?image=lock6li.jpg)

---

### Post by dtfinch on 2005-11-07
I experience the same annoyance on Windows. Maybe they're trying to "be like Windows", or maybe they're just trying to be consistent by always having copied files have the same permissions at the destination as they had at the source, 555 in the case of a CD that stores no permissions and thus is always considered read only and executable.

---

### Post by bionnaki on 2005-11-07
so, is there any way to have to have full user permissions on any cd you put into the drive (or rather, the files you copy to your harddrive)? or is it pretty much default to have all discs 555?

I am just confused - I just dont recall this happening before...

---

### Post by essexman on 2005-11-12
[quote=bionnaki]so, is there any way to have to have full user permissions on any cd you put into the drive (or rather, the files you copy to your harddrive)? or is it pretty much default to have all discs 555?

I am just confused - I just dont recall this happening before...[/quote]

This may be a general problem that users are having reading and writing to DVDs. See [here]("http://ubuntuforums.org/showthread.php?t=84541&highlight=dvd-r") and [here]("http://ubuntuforums.org/showthread.php?t=77662&highlight=dvd-r") and [here.]("http://ubuntuforums.org/showthread.php?t=84971&highlight=dvd-r")  No-one is posting any real answers yet, but I'm sure they will soon; please keep posting.

---

### Post by bionnaki on 2005-11-12
all other discs can transfer to ubuntu just fine - only that one disc creates odd permissions. no idea why.

---

### Post by darknuala on 2005-11-13
When you set up your Documents folder in Windows, did you set the permissions to be read by only your username?  Such as when it asks if you want to keep your files private?  This has on occasion screwed around with access to them in linux with my experience.  Did you try copying the files to your drive, then chowning them under your username?

Also could it be the files are read-only?  I had a music folder called mp3 that i copied to my hd.

I did a sudo chown username /home/username/mp3, and it worked

---

