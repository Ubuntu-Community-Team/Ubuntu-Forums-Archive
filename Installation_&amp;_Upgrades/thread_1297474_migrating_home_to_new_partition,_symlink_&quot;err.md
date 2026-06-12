---
title: "migrating home to new partition, symlink &quot;errors&quot; found by diff"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by wamanning on 2009-10-21
i'm following these instructions to move my home directory to a dedicated partition:

[INDENT][https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)[/INDENT]

[INDENT][FONT="Courier New"]sudo rsync -axS --exclude='/*/.gvfs' /home/. /media/home/.[/FONT][/INDENT]

i used the rsync command to copy the files over.  subsequently i'm using diff to double-check the copy against the original and i'm getting what *appears* to be missing symlinks, or at least symlinks that seem funky.  here are the errors, and now i notice i'm getting similar errors from *both* old and new versions.  strange.

[INDENT][FONT="Courier New"]diff: /home/user1/.kde/cache-computer1: No such file or directory
diff: /home/user1/.kde/tmp-computer1: No such file or directory
diff: /home/user1/.pulse/ce27733e29790957d96b1e174ad2e3d7:runtime: No such file or directory
diff: /homeOLD/user1/.kde/tmp-computer1: No such file or directory
diff: /homeOLD/user1/.kde/cache-computer1: No such file or directory
diff: /homeOLD/user1/.pulse/ce27733e29790957d96b1e174ad2e3d7:runtime: No such file or directory
[/FONT][/INDENT]

poking around the *new* home partition, the corresponding directories that these symlinks reference do not exists:

[INDENT][FONT="Courier New"]/var/tmp/kdecache-user1
/tmp/kde-user1
/tmp/pulse-goIcwN0rvoq2
[/FONT][/INDENT]

strange.

any idea what i should do with these if anything?  maybe some old/leftover symlinks from my recent, from-scrach, 9.04 install?

---

