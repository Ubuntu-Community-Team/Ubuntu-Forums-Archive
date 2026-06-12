---
title: "Files gone?"
date: 2008-07-12
forum: General Help
---

### Post by benign on 2008-07-12
I'm not exactly sure where my files went, but they seem to have disappeared. I went into my home/user/music dir and made a sym link from the terminal with ln -s /media/HP/Music and then a link showed up to that directory within user/music. After that I moved the sym link into my home dir, overwriting the "music" folder that was already there - only it didn't overwrite anything, it just deleted the original music folder and the sym link that was inside of it. So then I made another symlink to the /media/HP/Music in the home folder, and it made a link to an empty directory! I checked the other hard drive, and all of my music files are gone.

I just searched both hard drives for the music, and it's all gone. 

Can someone explain exactly how I screwed up there?

---

### Post by Taxman415a on 2008-07-12
It's hard to tell without knowing exactly the commands you entered. You could pull them from the contents of your .bash_history file. In the meantime, if you really did delete your data it's important not to write anything to that drive to minimize the chance that you overwrite any of the deleted data. If you don't overwrite any of it, there's a good chance you can recover some or all of it. So unmount the drive the music is stored on or at a minimum remount it read only. What filesystem is it? (ext3, ntfs, etc)

---

### Post by benign on 2008-07-13
> **Taxman415a said:**
> It's hard to tell without knowing exactly the commands you entered. You could pull them from the contents of your .bash_history file. In the meantime, if you really did delete your data it's important not to write anything to that drive to minimize the chance that you overwrite any of the deleted data. If you don't overwrite any of it, there's a good chance you can recover some or all of it. So unmount the drive the music is stored on or at a minimum remount it read only. What filesystem is it? (ext3, ntfs, etc)


The media with the music on it is NTFS. I just did this again with another directory as a test, and it may be a bug because it removed every file from the symlinked directory again. This is exactly what I did:

1) Created a symlink to a directory on the NTFS volume inside of /home/user/Music from the /home/user/Music directory using "ln -s /media/HP/directory"

2) Renamed the symlink to "Music"

3) Right clicked the symlink to Music and selected "Copy"

4) Went up one directory into /home/user and selected "Paste" (to overwrite the REAL directory with the SYMLINK)

5) It asked to overwrite; I clicked "Yes"

6) An error dialog comes up saying that the file does not exist.

7) Check the REAL directory on the NTFS volume - all files are gone.

The funny this is that it doesn't delete the original directory, but only the files in the directory. The system encounters an error when trying to overwrite a real directory with a symlink, and seems to end up just deleting all the files from the real directory!

I tried doing this on the ext3 volume, and it ends up creating a single 17 byte link file and deletes the original directory (which in this case should be expected because I'm actually overwriting an entire real directory). If I try to open the link file it tells of "looping links."

The console appears to be a bit smarter than the GUI. If I try to do all of this from the console, even with the force switch, it tells me I can't overwrite a directory with a non-directory and the original files remain in the real directory. Ignoring the warning of the console and doing it in nautilus results in all of the files within the directory being deleted.

---

### Post by Taxman415a on 2008-07-13
Ok, it took me a bit to figure out what you had done since it was hard to tell which were the console commands and which were the Nautilis (the gui file manager) commands. It would help a bit if you put in the shell prompts something to the effect of
```
user@foo:~/Music$ ln -s /media/HP/directory
```
that way it can be seen which directory you were in (~/Music). Only reason I'm saying this is to make the reports clearer to someone else.

In any case it looks like you have found a bug in the way Nautilus handles simlink copying and overwriting. I was able to test it and get the same behavior. I even did the whole process all in the gui (a little tricky to do, which is probably why the bug hasn't been squashed yet) and it worked the same. It's probably not an Ubuntu bug (Nautilus is a Gnome package), so it's probably best to file the bug report directly with Gnome. They may tell you it's already been fixed in the latest Gnome.

---

