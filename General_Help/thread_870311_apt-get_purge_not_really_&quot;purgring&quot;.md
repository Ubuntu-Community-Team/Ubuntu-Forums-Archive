---
title: "apt-get purge not really &quot;purgring&quot;"
date: 2008-07-25
forum: General Help
---

### Post by Phastor on 2008-07-25
I must have a misunderstanding on how this command works.  I'm under the impression that it's supposed to wipe out everything that has to do with whatever package you are purging.  However every package I have removed this way (or with just apt-get remove) always still leaves behind configs and other hidden files in my home directory.  Is purge supposed to get rid of these?  I've noticed after removing Wine, easytag, cedega, and several other packages these hidden directories remain.  Is there a way to get rid of them, or can I just safely delete them after purging the packages?

---

### Post by rbmorse on 2008-07-25
They can be safely deleted from ~/home

The purge command should remove setups and other configurations from /etc, especially lines that get inserted into the /etc/init.d and /etc/rcX.d folders.

---

### Post by Rocket2DMn on 2008-07-25
The correct command to run is
```
sudo apt-get remove --purge <package>
```
Is that what you have been doing?

Also see [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

---

### Post by wkulecz on 2008-07-25
As far as I know its alwyas safe to delete these application specific hidden directories in your home folder as long as you are willing to lose any settings or data stored there.  They will be recreated next time the applicaion runs.

That's why apt can't delete them, apt runs as root, you run the apps as username, so apt doesn't know where they might be.

--wally.

---

### Post by scragar on 2008-07-25
technicaly purge should remove config files, the problem however is that apt is unable to tell what user is uninstalling it, so it actualy leaves the config files.
They are safe to delete, not sure if it's possible to get it to remove config files for anyone other than root(which most packages do)

---

### Post by silkstone on 2008-07-25
Purging removes files in system folders but it may leave some config files in your home directory. A few people have had problems with Firefox recently, where purging and reinstalling hasn't cured a problem, and it's because the original (probably corrupt) configuration files were still in the .mozilla/firefox folder.

If you are absolutely sure that a folder/directory within your home folder is no longer needed, you can delete it.

Sometimes people want to do a complete reinstall of the software, but still keep configuration, database files, etc that are in their home folder, so I think that's why these are not removed.

---

### Post by Phastor on 2008-07-25
Thank you for the help.

I wanted to wipe out all configs and everything for wine because I screwed it up and wanted a completely fresh install of it.  I wanted to completely remove Cedega with no intention of using it again, so no problem losing configs there.  I wanted to remove Easytag because I installed both it and Picard to see which I liked better.  So again, no problem losing the configs there since I liked Picard better.  Nice to know I can safely remove these directories now.

Thanks again for the help.

---

