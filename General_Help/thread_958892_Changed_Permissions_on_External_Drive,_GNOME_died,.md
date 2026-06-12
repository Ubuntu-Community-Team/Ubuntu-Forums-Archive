---
title: "Changed Permissions on External Drive, GNOME died, and Now Cannot Login"
date: 2008-10-25
forum: General Help
---

### Post by zerted on 2008-10-25
I have a 250GB external USB drive that I use to make backups.  In the past, I've put on it random copies of folders (half the time as root).  Today I copied my entire home folder to it.  I wanted to go through the entire drive to better organize the backups and remove any duplicated files.  Since the folders had inconsistant permissions, I decided to make them all fully readable and writable (its an external backup drive, why not?).

I opened the drive using a right click 'browse as root' script, selected all 17 main folder/files, right clicked, selected properties, then viewed the permissions tab.  I gave all users all permissions and applied to all folders/files.  A prepairing file operations window opened up with a bunch of operations starting and then GNOME died.  It pop-up something saying one of the panel tools failed and needed to be restarted, then all the text and icons became corrupted.  Most of the panel icons turned into red Xs, all the desktop icons turned into some simple icon, and all the text turned into squares.  A few more pop-ups showed up, but since I can't read squares, I don't know what they said.  

I left the permission operations finish and attempted to reboot the computer (even the shutdown dialog had no icons and no readable text, I think I guessed wrong and picked log-off...) 

To my surprise, I got a blue screen!  It said something like xwindow had restarted X times within X seconds and suggested there was a problem.  I held the power button to reboot the Lenovo X61 Tablet.

When it restarted, it only booted up to a command line login.  I attempted to login, but it said 'Unable to cd to '/home/zerted'.  I rebooted and used the recovery features to get a root prompt.  A quick look around my home folder and the root structure and everything seems fine...

What happened, why can't I login as the normal user, and how should I go about fixing it?  

[SIZE="1"]It seems that whenever I backup my system, it breaks (had hard drive corruption on my Windows machine last time I backed that up)[/SIZE] :mad:

---

### Post by geirha on 2008-10-25
If you change permissions on a symbolic link, it will change the permission of the file or directory it is pointing to. It is possible that you had a symbolic link pointing to a certain file or directory that made things break when you changed the permissions. I'm guessing it was a link to your home-folder, and I'm guessing it was given read and write permissions for everyone, but not execute permissions. If you want to cd into a directory, you need execute permissions for it. Could be this the case? what's the output of ```
ls -ld / /home /home/zerted
```

---

### Post by zerted on 2008-10-25
> **geirha said:**
> Could be this the case? what's the output of ```
ls -ld / /home /home/zerted
```That sounds like it could be the problem.  I didn't change the execute field in the permissions tab.  Just assumed it wouldn't chagne it since I didn't change it...
The output is```
drw-rw-rw- 21 root root 4096 Oct 25 10:28 /
drwxr-xr-x 6 root root 4096 June 25 18:40 /
drw-rw-rw- 103 zerted zerted 4096 Mar 13 2008 /home/zerted
```

I tried *chmod u+x /home/zerted* (and then *a+x*) as root, but it didn't fix the problem.  Assuming that this is the source of the problem, if I remount the backup drive and make everything executable, then it should follow the same links and fix everything correct?

I forgot to mention, sometimes it hangs on ** Starting Hardware abstraction layer hald* when booting.  There are also a few other 'fail' that show up to.

---

### Post by geirha on 2008-10-25
Ouch, / is not executable and writeable to all, and that may indeed cause alot of problems.
```
sudo chmod 755 / /home/zerted
```

You should mount the drive and check what symbolic links there are and what they are pointing to. If they are pointing to someplace outside /home, you should check the permissions on that, and either compare with the permissions the same file/folder has on the livecd, or reinstall the package that isntalls the file/folder.

This should give you a list:
```
sudo find /media/backupdrive/ -type l -ls
```

---

### Post by zerted on 2008-10-25
> **geirha said:**
> Ouch, / is not executable and writeable to all, and that may indeed cause alot of problems.
```
sudo chmod 755 / /home/zerted
```That allowed GNOME to come up and me login.  My desktop was missing, but making it executable fixed that.  I was going to start fresh with 8.10 when it comes out, so I'll just skip the permission recovery and keep the laptop off the net until then.

Thanks a bunch, I didn't expect to get it usable tonight \\:D/

---

