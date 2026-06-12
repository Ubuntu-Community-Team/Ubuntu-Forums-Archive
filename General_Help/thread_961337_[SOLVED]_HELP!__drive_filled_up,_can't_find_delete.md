---
title: "[SOLVED] HELP!  drive filled up, can't find deleted files"
date: 2008-10-28
forum: General Help
---

### Post by ChrisC on 2008-10-28
Oh boy, I'm getting into worse and worse trouble here and I need help.

Short version:  files deleted as root have disappeared (not in root .Trash) but seem to still be taking up space

Long version:

I tried to do a regular full backup last night.  Sbackup created much bigger backup files than usual, and I'll have to figure out what went wrong there.  In the process of starting and stopping sbackup, it created a few backup folders, which I deleted.

I have my backup folders stored in /home/myusername/backup [1], and then have the backup folder owned by root, I think because sbackup insisted on it.  So to see into the backup folder, I have to "sudo nautilus".  From there I can delete older unneeded backup folders.

When I do that deletion, in nautilus as root, I would expect the folders to then appear in the root Trash (aka /root/.Trash), and I figured out about a year ago that I need to clean that out to reclaim the space.

But now I can't empty the root Trash, nor even navigate to it!  Running Nautilus as root, when I click on Trash it says "the folder contents could not be displayed" .  And indeed even if I use the command prompt, I find that there is no /root/.Trash folder or anything similarly named.

I did clean out my regular user trash.

Now, recall that I HAD deleted some backup folders while in nautilus as root, so they went somewhere.  df says the partition is still full, so they're lurking somewhere.  The system is starting to do Bad Things because the partition is full, and I'm actually typing this on another computer.

I forced a fsck and it didn't find any problems, and I'm still 100% full on my home partition with files that I can't find :(

Help!

[1] backup is not in var because /home is where all my hard drive space is

[2] what is the command for the graphical Disk Usage Analyzer so I can run it as root?  it's not baobob.

---

### Post by plucky on 2008-10-28
This [thread by DRS305](http://ubuntuforums.org/showthread.php?t=898573&highlight=clean+hard+disk) might help.

I think with your backup,as you are copying to your /home/username/backup folder,sbackup also backs up /home,so you are copying the backup into your backup and so on until your home folder fills up.That is why sbackup uses /var/backup.

Just a thought.

---

### Post by ChrisC on 2008-10-28
Great link, thanks plucky!  I'll try it out tonight when I get back to that computer.

I'm aware of the recursion problem you described.  I explicitly excluded the /home/username/backup directory in the sbackup config.  But maybe it's ignoring it now for some reason.  Anyway, I'll be able to figure that out once I get some freaking wiggle rooom on that system :)

---

### Post by ChrisC on 2008-10-28
And that worked!  The files were in /home/.Trash ; I had been looking for /root/.Trash , which is where they used to be (I think).  Oddly, I don't think Disk Usage Analyzer found them there.

I used to back up all of /home and selected subdirectories of /etc, /var and so forth.  The idea was that there might be things outside of /home/chris (like system config files) that I might need to restore.  But that's more trouble than it's worth, and I'm going to now just back up /home/chris and move on ...

Thanks again!

---

