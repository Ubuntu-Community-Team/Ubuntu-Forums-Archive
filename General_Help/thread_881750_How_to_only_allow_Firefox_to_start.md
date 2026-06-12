---
title: "How to only allow Firefox to start"
date: 2008-08-06
forum: General Help
---

### Post by AlmightyNinja on 2008-08-06
Hellow I have been wondering if there is possibility to only allow firefox to run on Xubuntu or that only firefox icon would be on desktop and nothing else. I tried Pessulus to lock down saving on disk and starting terminal but it doesn't work I can still do pretty much everything even with unprivilleged user account.  This computer would be used for public users. I tried R-Kiosk extension for FF but that's to much limited. Any help would be much appreciated. Thanks.

---

### Post by mb_webguy on 2008-08-06
Have you looked at [KioskCD]("http://www.kioskcd.com")?  It's a Linux distribution that runs off of a CD, and opens up Firefox in kiosk mode.  It's made specifically for the sort of thing you're describing, and it would be a lot easier than trying to lock down Xubuntu.

---

### Post by AlmightyNinja on 2008-08-06
Well I would still like navbar and bookmarks toolbar in firefox and  that it would start from hard drive.

---

### Post by mb_webguy on 2008-08-06
You can install KioskCD so it boots from the hard drive.  I still think this is your best option, because otherwise you have quite a bit of work to do to make sure the system is locked down tight.  Of course, KioskCD is a bit out of date, so before you install it you might want to open up the ISO and edit it a bit, such as installing Firefox 3.

However, if you're really not interested in using KioskCD, I can suggest a few steps to take to lock down your system.  I'm not familiar with XCFE, so I'll say how I'd go about doing it in Ubuntu with Gnome, and maybe you can apply some of it to XCFE.

First you should make a new user account.  Drop the user from any unnecessary groups.  You definitely need to make sure the user isn't in the admin group.  

Next, you should probably disable ctrl-alt-delete.  I don't know how to disable it for a single user, but you can disable it for all users by following the instructions in the last couple of posts in [this thread]("http://ubuntuforums.org/showthread.php?p=2181001").

You also need to disable the ctrl-alt-backspace combination, which you can do by following the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=146590").  Again, this will unfortunately apply to all users.  Alternatively, if XCFE has the option to automatically login a user without a password, you could set that, so even if the user restarts X with ctrl-alt-backspace, it will just log him back in.

Go ahead and put a Firefox shortcut/launcher on the desktop.  If you have icons on the desktop for drives or the home directory, remove them.

Now either edit the menu and remove or hide all programs you don't want the user to have access to, or remove the panels/menus entirely if you don't want the user to have access to anything but Firefox.  You definitely don't want to leave the user any easy access to the terminal or any kind of administrative functions.  This is relatively easy to do in Gnome, but I don't know about XCFE.

This should be a good start to locking down the system, and will keep the casual user from doing anything you don't want them to do.  But this still won't keep knowledgeable users from coloring outside the lines.  For example, you can still hit ctrl-alt-f1 to drop into a command line, and I'm not sure how you can disable that.

---

### Post by AlmightyNinja on 2008-08-07
Thank you mb_webguy for this useful post. Can anyone tell me why this message appears when I start Pessulus:
(pessulus:27084): GConf-WARNING **: haven't implemented getting a specific locale in GConfClient

What have I done wrong? Thanks in advance.

---

### Post by AlmightyNinja on 2008-08-08
I got that message in Ubuntu.

---

