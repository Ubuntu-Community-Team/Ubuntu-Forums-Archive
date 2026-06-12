---
title: "access fedora home folder from within ubuntu"
date: 2008-08-06
forum: General Help
---

### Post by AltairJr on 2008-08-06
I have seen a few methods posted for accessing the folder, but being a new user to linux in general (let alone ubuntu) I can't be sure why I can't access my fedora home folder.

I have successfully mounted the partition under /mnt/fc9 after installing lvm2 -just don't have the permissions to access the home folder

tried using chown to change ownership but on all the files i get the message read-only file system

for the record - work doesn't give me a whole lot of time between working and sleeping for the next month or so so I don't have a lot of time to study how to re-access fedora (ubuntu was installed last night and for the time being can't boot into fedora)

that being said the method of changing the uid or something inside fc9 and also in ubuntu is not available (it also seems a rather clunky method of doing it in the first place :p)

all i want to do is to pull some media files (music, manga, movies) from the fc9 partition so I can then reclaim that space and use it for ubuntu and so as long as I can get those files, I'm not worried about any methods that may break fc9

Any help is greatly appreciated

---

### Post by RealPSL on 2008-08-07
It would seem like your file system was mounted read-only. Did you run fsck on it before you mounted it?

---

