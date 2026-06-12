---
title: "A Backup Utility Similar To Time Machine?"
date: 2008-08-27
forum: General Help
---

### Post by vjkeito on 2008-08-27
I've had a look at Flyback, Timevault, Hubackup, Sbackup, Simplebackup and various others.

Flyback looks great but for some reason development appears to have stopped.

What package/project is the best choice for a regular system backup, that is stable and not going to die a death any time soon?

---

### Post by mellowd on 2008-08-27
rsync, tar

---

### Post by eldragon on 2008-08-27
> **mellowd said:**
> rsync, tar

freakin helpful.


what he meant is: many backup solutions come as scripted cronjobs involving rsync / tar

i personally use rsnapshot (which uses rsync), and let it take advantage of hardlinks for incremental backups (aka, same file, copied multiple times, takes up space for 1 file). its in the repos, its quite simple to setup but its going to be much more ugly than time machine. (no gui).

let it run nightly and allow it to backup essential parts of my system (/home /etc) the rest i can reinstall in the event of the unforseen... :D

hope i helped :D

---

### Post by sameerds on 2008-08-27
> **eldragon said:**
> i personally use rsnapshot (which uses rsync), and let it take advantage of hardlinks for incremental backups (aka, same file, copied multiple times, takes up space for 1 file). its in the repos, its quite simple to setup but its going to be much more ugly than time machine. (no gui).

Most important "feature" of rsnapshot, or in general anything that uses rsync is that the backed up data is "right there" in front of you. No fancy formats, no compression, nothing. Just cd to the backup directory and copy whatever you need. The flip side of that is it doesnt work very well with FAT file systems, but no problems with NTFS.

---

### Post by vjkeito on 2008-08-27
Well I did/do know about rsync and tar but what I would like is some seriously user friendly package that has an intuitive GUI that requires little knowledge of linux systems or the commandline.

I like getting my hands dirty, but I also have a girlfriend and mum who use ubuntu.  I am looking to install a package that they can use also so just stating rsync and tar won't really cut the mustard there, though thanks for pointing them out.

Both Timevault & Flyback look like they are pretty intuitive and I'd be using Flyback right now if I thought that it had a future.

Does anyone know why such a promising app came to an end?  Did apple shake the tree?

---

### Post by DGortze380 on 2008-08-27
> **vjkeito said:**
> Well I did/do know about rsync and tar but what I would like is some seriously user friendly package that has an intuitive GUI that requires little knowledge of linux systems or the commandline.

I like getting my hands dirty, but I also have a girlfriend and mum who use ubuntu.  I am looking to install a package that they can use also so just stating rsync and tar won't really cut the mustard there, though thanks for pointing them out.

Both Timevault & Flyback look like they are pretty intuitive and I'd be using Flyback right now if I thought that it had a future.

Does anyone know why such a promising app came to an end?  Did apple shake the tree?

No idea about what kind of GUI programs are available, but I would just put the rsync and tar commands into scripts. Either load it into cron, or just give them the script, make a launcher for it on the desktop. Double click to backup.

Restoring could be a little more tricky but again could be accomplished with a simple script.

---

### Post by sameerds on 2008-08-27
> **vjkeito said:**
> Well I did/do know about rsync and tar but what I would like is some seriously user friendly package that has an intuitive GUI that requires little knowledge of linux systems or the commandline.

Makes sense. But consider this. A backup job is supposed to be:
[LIST=1]
[*] non-intrusive
[*] completely invisible
[*] reliable
[*] easy to recover
[/LIST]

In that case, rsnapshot is the best thing to have. You set it up once, by editing a single file, and you never look at it again. Backups just magically appear in your backup location at regular intervals. Recovering is easy ... all you have to do is go to the backup location and copy. The user could use a graphical file browser for doing that just as well.

Just the fact that you expect your mom and girlfriend to understand what a backup is, and to learn a GUI tool to manage it means that you are doing it wrong.

As I see it, the only current shortcoming of rsnapshot is that it does not guarantee data integrity. When rsnapshot says that it has rsynced your data on schedule, it has not verified the copy. I have been wondering about extending rsnapshot to do checksums, but I am not an expert, and would need some time to get up to speed. If there is a tool which is as good as rsnapshot, and also does checksums, I would love to hear about it.

---

### Post by sameerds on 2008-09-03
> **sameerds said:**
> As I see it, the only current shortcoming of rsnapshot is that it does not guarantee data integrity. When rsnapshot says that it has rsynced your data on schedule, it has not verified the copy.

Well it turns out that I was wrong on this one. rsync already uses an after-the-transfer checksum for data verification. From the manpage:

[INDENT]Note that rsync always verifies that each transferred  file  was correctly  reconstructed  on  the receiving side by checking its whole-file checksum[/INDENT]

Which means rsnapshot is all of the above: reliable, unobtrusive, invisible and easily recoverable! Couldn't ask for more from a simple desktop backup utility.

---

### Post by grigio on 2008-11-01
All gui projects seem dead :twisted:

Is so difficult to do a fuc**ng gui to rsync + inotify?

---

### Post by rbmorse on 2008-11-01
Try it and see.  I'll check back in a month to see how you're doing.

---

### Post by scouser73 on 2008-11-02
What I have done with my PC is to have all the things I have downloaded from the repositories burnt onto a CD from a program called APTonCD; [http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/) once you have installed and done the necessary tasks, you should then install Remastersys, which makes a ISO backup of your system; [http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

Both are extremely easy to use, it took only 20 minutes to have everything back up and running as normal again.

---

### Post by sefs on 2008-11-04
Timevault from this write up ... [http://www.linux.com/feature/150600](http://www.linux.com/feature/150600) ... looks pretty good.

---

### Post by gjosef on 2008-11-10
> **sameerds said:**
> In that case, rsnapshot is the best thing to have. You set it up once, by editing a single file, and you never look at it again. Backups just magically appear in your backup location at regular intervals. Recovering is easy ... all you have to do is go to the backup location and copy. The user could use a graphical file browser for doing that just as well.

Sounds good so far. But suppose I've set it up to run automatically once a day, how do I find out when it suddenly stumbles upon a problem and fails to run? Can I obtain an email report or something? Or would I need to browse through log files every now and then...

---

