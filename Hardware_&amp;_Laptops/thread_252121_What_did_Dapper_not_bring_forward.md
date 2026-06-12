---
title: "What did Dapper not bring forward?"
date: 2006-09-06
forum: Hardware &amp; Laptops
---

### Post by Guns90 on 2006-09-06
I'm trying to use my Creative ZEN Nano Plus (1GB) MP3 Player with Dapper.  It used to work fine with Breezy.  Now it is recognized by Dapper as a usbdisk, and it transfers files 'IN' and 'OUT' (until it reached it's capacity). It plays all the files in it just fine, My problem is that I can not remove files from it to provide space to install new files.  This player still works fine in Windows.  I did a clean install of Dapper.  Appearantly, Dapper changed something or did not include something that Breezy had in it.  A search has not found a salution. (msak007's thread did not help; it's for the Jukebox not the ZEN Nano Plus). Anyone got any ideas?

---

### Post by meng on 2006-09-06
Try browsing in Nautilus and press ctrl-H to see hidden files. I wonder if you have a .Trash (or specifically a .Trash-username) directory holding those "deleted" files. If so, change your Nautilus preferences to allow a "Delete bypassing Trash" or some such option that can then be invoked with Shift-Del.

---

### Post by Guns90 on 2006-09-06
Sorry I didn't get back to you sooner.  I'm a noob, so how do I 'browse' Nautilus?  

I do have a .trash file showing up in the player.  (I saw it when using windows.)

---

### Post by galileon on 2006-09-06
he meant just opening the usb disk icon that appears on your desktop, and click View>Show Hidden Files...

anyway, in windoze, try to see if the deleted files are being stored in .Trash, and delete them...

---

### Post by Guns90 on 2006-09-06
I deleted all the MP3 player files using windoze and came back into ubuntu. The usbdisk activates when I plug it in, I can transfer files into the player, and play them (both through the computer or just the player); however, if I 'move to trash' a file, it disappears, but does show up as a 'hidden file'.  I'd like to be able to do everything in linux.  

I'm still a bit confused on changing the preferences in Nautilus.

---

### Post by meng on 2006-09-06
Nautilus is the file browser in GNOME, so by looking at files you are using Nautilus. There should be a Preferences menu in the toolbar of the file browser, and I think the option you need to activate is in the Behavior tab.

---

### Post by Guns90 on 2006-09-07
Sorry I took so long getting back to you galileon and meng.  Now that I have the hidden files showing, I'm happy with everything.  Thanks a lot guys.

---

### Post by Guns90 on 2006-09-09
I have another thing that is bothering me that I used to be able to do in Breezy, but can't in Dapper; monitor my sensors.  At bootup, I get a 'Setting Sensors Limits' 'Failed'.  There are several threads on the forum concerning this subject, and I have followed three of them, but I have yet to be able to correct the problem.  All of these threads are exhaustive to someone who doesn't understand the intricacies of computers.  I just believe that this has to be something that was an oversight on the update from Breezy and should have an easy fix.  Maybe I'm wrong.  If anyone has a fix I'd sure appreciate it.  Thanks

---

