---
title: "how to make alert button that pops up on Desktop?"
date: 2008-11-19
forum: General Help
---

### Post by quixote on 2008-11-19
Anacron runs a reminder script.  When it does, I want a nice red button to appear on the desktop. But I can't find a command line way to associate a specific icon with a desktop link.   The longer version of the problem is this:

I have backups scheduled via anacron.  However, even with the time delay, as often as not, it's trying to run them at bad times.  So I thought a clever solution would be for anacron to just run a reminder script.  The reminder would pop up a red button on the desktop and be a link to the actual rsync backup script. So what anacron runs is this:
```
ln -s /home/quixote/backup.sh /home/quixote/Desktop/backup.sh
```
Clicking on that runs the backup shell script.  But the link on the desktop is just the bland little thing for that mimetype, and I don't want to change that.  I.e. I don't want all shellscript files to have a red button icon.

Also, once clicked, I want the icon to disappear until the next time anacron runs the reminder.  I haven't figured out how to do that at all! :(

Is there a way to tell "ln" which icon to use?  Or is there a completely different and better way to do a desktop alert button that links to a shell script?

---

### Post by quixote on 2008-11-20
(I'll try this question in General or Beginner Talk, since it looks like I may not be in the right forum.  If you do have an answer for me, please let me know!  I'll keep watching this thread for a few weeks.)

---

