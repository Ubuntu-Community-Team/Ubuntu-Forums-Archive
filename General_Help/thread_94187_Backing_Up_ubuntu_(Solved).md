---
title: "Backing Up ubuntu (Solved)"
date: 2005-11-23
forum: General Help
---

### Post by lysis on 2005-11-23
I already know how to backup certain aspects of Windows, but how do you backup certain aspects of Linux?

Say I want to backup my Mozilla Firefox passwords, or emails from Thunderbird, or just basic things like my settings for my toolbars on the desktop (not using any third party programs -- just positions, transparencies, icons that are placed, etc)

I've installed K3b and verified it's working on my system. I am running gnome; is there a software DESIGNED for gnome for burning data? I am in the understanding K3b was DESIGNED for KDE.

Thanks guys

---

### Post by Roman27 on 2005-11-23
[QUOTE=lysis]I've installed K3b and verified it's working on my system. I am running gnome; is there a software DESIGNED for gnome for burning data? I am in the understanding K3b was DESIGNED for KDE.[/QUOTE]

Try GnomeBaker.

---

### Post by lysis on 2005-11-23
Sounds good. I'll give that a try when I get home. 

Any ideas as to how to backup these things?

---

### Post by lysis on 2005-11-23
no ideas for backing up files??

---

### Post by professor_chaos on 2005-11-23
how I interpret your thread is just that you wanted a program to burn copies of files on your system and thus making a backup. But if you want all of this to happen automatically, I haven't found a program on linux to do so. At least to make an incremental backup to CD or DVD. 
I do however have my system running a script daily to backup important directories to another harddrive. I use rsync for this purpose. 
If you find a program to make backups to cd or dvd, let me know.

---

### Post by Kevinator on 2005-11-23
All your personal files and settings should be located in /home/YourUserName. This should include Firefox passwords, email, and toolbar settings. Typically these things are stored in hidden files or folders. For example, Firefox stores everything in a folder called /home/YourUserName/.mozilla. Note that the dot at the beginning of a file or folder name is the *nix way of making it "hidden". These files and folders are typically not displayed by default, but can be seen with extra options (such as the -a flag for ls), or the Show Hidden Files option in Nautilus's View menu).

HTH.

---

### Post by ubuntu_demon on 2005-11-24
There will be something easy in the future :
[https://wiki.ubuntu.com/HomeUserBackup](https://wiki.ubuntu.com/HomeUserBackup)

In the meantime you can just try to burn your entire /home including hidden files and excluding big stuff like movies and music.

Or you can try dar and see whether you'll like it (I haven't tried it so I have no idea how user friendly it is but the developers are thinking about using it for the backup tool).

description about dar :
$apt-cache show dar

to install dar :
$sudo apt-get install dar

---

### Post by lysis on 2005-11-24
that's the info i was looking for!

thanks a lot for your help guys. i know how to burn a disc, just wasn't 100% sure where the files were stored (since when i do ls -l -- the only ls command i know haha it doesn't show up)

---

### Post by nilfilter on 2005-11-24
Well, just for the record:

You might want to give [SBackup]("http://sbackup.sourceforge.net") a shot. 

Excerpt from its home page:> SBackup is a simple backup solution intended for desktop use. It can backup any subset of files and directories. Exclusions can be defined by regular expressions. A maximum individual file size limit can be defined. Backups may be saved to any local and remote directories that are supported by gnome-vfs. There is a Gnome GUI interface for configuration and restore.
I haven't tried it myself yet, though.

---

### Post by pappo on 2005-11-24
Here is a good website with help for backups using Linux:

[http://www.linux-backup.net/App/](http://www.linux-backup.net/App/)

---

### Post by Randy Sparks on 2005-11-24
I've used Sbackup and can confirm that it's seems bug-free and works very well. It's fairly simple as to how it works and it appears in your System - Administration menu. It's available via Synaptic.

It's a new piece of software that came from the Google Summer of Code 2005 sponsorship programme. Some Ubuntu engineers helped out too, it seems.

I suspect Sbackup will appear in the next version of Ubuntu as the de facto backup program so we should all be using it to try it out.

---

### Post by coaxx on 2005-11-28
..and for dar there is a nice KDE frontend kalled KDar.

---

### Post by steevc on 2005-11-29
I've been trying to work out how to use [http://sbackup.sourceforge.net/HomePage]("http://sbackup.sourceforge.net/HomePage")

I want to store my backup on a remote server over ssh. When I run the sbackup set-up it has a path of

ssh://username:password@example.com/remote/dir/

but when I try something similar with appropriate values for my server it says it is not writable. It could be that it's not even connecting. Is this the correct format? I don't know that much about ssh, but I assume it shoudl extract the username and password from the URL and pass them securely.

Any ideas? I'm running KDE rather than Gnome, but I don't think that should affect this process.

It really is about time I set up proper backups.

---

### Post by paritybit on 2006-04-24
[QUOTE=steevc]
I want to store my backup on a remote server over ssh. When I run the sbackup set-up it has a path of

ssh://username:password@example.com/remote/dir/

but when I try something similar with appropriate values for my server it says it is not writable. It could be that it's not even connecting. Is this the correct format? I don't know that much about ssh, but I assume it shoudl extract the username and password from the URL and pass them securely.
[/QUOTE]
I have been having the same problem... not sure what is causing it, just a bad example perhaps?

---

### Post by paritybit on 2006-04-24
Looks like they know about this and will have it fixed for V1:
From [http://sbackup.sourceforge.net/SBackupRoadmap](http://sbackup.sourceforge.net/SBackupRoadmap) :
resolve remote writability testing problem
[https://sourceforge.net/forum/forum.php?thread_id=1402351&forum_id=486192](https://sourceforge.net/forum/forum.php?thread_id=1402351&forum_id=486192)

---

