---
title: "Hellanzb permissions problem"
date: 2008-10-24
forum: General Help
---

### Post by sab0tage on 2008-10-24
I don't know why, but ever since I format my extra 500GB drive from NTFS to ext3, completed files downloaded using hellanzb have only rw access by owner, but no read access by group and others. So I am unable to access the files from my network. I can access ALL the files BEFORE the format from the network.


Files download BEFORE formatting drive (was NTFS)
drwxr-xr-x 2 ryan ryan 

After reformatting the drive to ext3
drwx------ 2 ryan ryan 

I'm having to ssh in and chmod the newly downloaded files so that I can access them over my network share. I don't understand? Why is the files being written with these permissions? If I download a file with Firefox, the permissions are fine, so I assume it is something to do with hellanzb.

:guitar:
EDIT:: Of course after several hours of trying to solve the problem on my own, I figure it out only after making this post.

```
# hellanzb inherits the umask from the current user's environment (unless it's
# running in daemon mode). The umask can be forced with this option
Hellanzb.UMASK = 0022
```

---

