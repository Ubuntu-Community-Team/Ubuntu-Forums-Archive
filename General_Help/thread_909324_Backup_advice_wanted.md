---
title: "Backup advice wanted"
date: 2008-09-03
forum: General Help
---

### Post by Xyem on 2008-09-03
Whoops, I just managed to issue an incorrectly typed rm command and managed to delete an unknown quantity of ( potentially important ) files off my server. ( For those curious, it was 'rm -rf *pTag* ~' ).

Luckily, I was running the drives in RAID1. I immediately took the second drive out of the array and currently have photorec running to recover the files. Also, it just happens that I ran sha512sum recursively through my entire home directory just yesterday which has survived the deletion, so I have hashes of all the files. I plan to cross-reference against the recovered files and, if I get them all, put them back where they were.

This encounter ( though not finished yet ) is too close for comfort. I would appreciate any backup advice anyone can offer. Is tape back-up a good idea/viable for a home user? I will also accept appropriate scoldings :(

---

### Post by joenix on 2008-09-03
It depends what you are looking for in your backup solution.

Currently I am using duplicity [1] to backup to a remote server. Since the backups are encrypted, you can even put your backups on an untrusted server.

Some other nice solutions are BoxBackup [2], rsnapshot [3] and rdiff-backup [4]. Two more experimental solutions are TimeVault and Flyback, that have Time Machine like functionality, but don't seem very stable yet.

[1] [http://www.nongnu.org/duplicity/](http://www.nongnu.org/duplicity/)
[2] [http://www.boxbackup.org/](http://www.boxbackup.org/)
[3] [http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[4] [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

---

### Post by Xyem on 2008-09-03
Online back-up won't be very useful in regards to uploading..

500GB ( current capacity [ & usage! ], upgrading to 1TB soon ) / 50kb/s upload = 121 *days* of constant uploading to mirror it. Ouch >.<

I was considering having another server next to the current one which could be woken up ( through the LAN would be easiest ) and then have that server rsync ( or similar ) the contents from the file/chat/etc server onto its own drives. While this wouldn't protect my data if the building burned down, it would protect it from me to a degree..

---

