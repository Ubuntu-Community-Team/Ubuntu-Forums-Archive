---
title: "Backup recommendation for dual boot"
date: 2008-10-16
forum: General Help
---

### Post by jmk123 on 2008-10-16
okay i have a dual boot dell with xp and kubuntu.  i am trying to kick the MS habbit, but sometimes i do need some of its features.  one of the apps that it has that i really like is a directory mirroring program.  i have one directory on an internal disk and an exact copy on an external.  when i add/delete a file in that directory, it gets mirrored to the external drive.  perfect. 

both are in fat32, so these same drives come up in linux.  is there a similar program in linux that does the same sort of thing without being overly complicated and without stepping on the toes of the xp app?  i know that rsync does this sort of thing, but it seems way overpowered for what i need.  also, it seems to complain that the backup directory already has files in it.

any suggestions? thanks!

---

### Post by ilrudie on 2008-10-17
What you are asking for sounds like a software raid mirror to me.  Maybe look into mdadm.  I'm not sure how well it will work with some random windows program writing to the mirrored disks though.

---

### Post by jmk123 on 2008-10-21
well, software raid is a little strong what what the xp prog does.  it just compares the local directory and remote directory every 24 hours.

if a file has been added to local, it adds it to the remote.  if you delete it from the local, it deletes it from the remote.  it's smart enough to do comparisons b/w similar files for size, creation, modification date, etc.  pretty simple.  

it keeps all it's r.c. files somewhere remote, so i don't have to worry about extra win files in the directories themselves.

something similar to this behavior would be great.  my concert with rsync is that if i modify the directories in my win boot, the new file will be in both the local directory and the remote directory when i go back to linux.  rsync doesn't seem to like this.

any suggestions?

---

### Post by ilrudie on 2008-10-22
Perhaps google the name of your windows application with linux alternative or ubuntu alternative and see what comes up.  Also [OSalt]("http://www.osalt.com/") may be helpful but I'd imagine google would find it if it was going to help.

Maybe look into [bacula]("http://www.bacula.org/en/").  Its a good backup client-server system that supports windows and linux clients and is free.

---

