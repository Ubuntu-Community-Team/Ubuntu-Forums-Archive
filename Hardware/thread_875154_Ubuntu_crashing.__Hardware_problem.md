---
title: "Ubuntu crashing.  Hardware problem?"
date: 2008-07-30
forum: Hardware
---

### Post by LuserName on 2008-07-30
I first started having this problem when I upgraded to 8.04.  I decided to reformat and try Debian Etch and had the same problem.  Finally I reinstalled 7.10 from my old disc and didnt upgrade to 8.04 and had no problems for about 2 weeks until yesterday when it crashed again while moving a particularly big folder of music from an external drive to my HDD.  The only time it has happened consistently is when trying to move this folder.  Usually it just happens when Im just browsing the web.

[http://uk.youtube.com/watch?v=Xz8y2gKezE4&fmt=18](http://uk.youtube.com/watch?v=Xz8y2gKezE4&fmt=18)

This is what happens.  All of a sudden the progress bar just stops and the only thing on my screen that will refresh is the estimated time (which keeps going up because its not actually doing anything).  I can move my mouse, but clicking doesnt do anything nor does alt tab or anything else.  Sometimes my icons will all disappear.  In the video first I hit ctr-alt-backspace and then I hit ctr-alt-F1 and neither is helpful at all.

Motherboard is made by Mach Speed, I can find the model if needed
Video card is a GeForce 8500 and Im using the restricted drivers
Pentium D 3.0 ghz
2 gb RAM which gave no errors when I ran memtest86 overnight

If anyone has any ideas, Id really appreciate it.

---

### Post by LuserName on 2008-07-30
Bump =\

---

### Post by LuserName on 2008-07-31
Bump

---

### Post by Sef on 2008-07-31
Bumping your thread is only allowed after 24 hours has gone by.  If you bump sooner, then you can be given an infraction.


> when it crashed again while moving a particularly big folder of music from an external drive to my HDD. The only time it has happened consistently is when trying to move this folder

This is a common problem with big folders.  If I find an answer, I will post it.  Otherwise, please wait for someone else to help you, or search in the fourms or use Google yourself.

---

### Post by LuserName on 2008-07-31
Sorry about that.  And the point is, it doesn't only happen when moving big folders, it happens seemingly randomly.  Since it started again, I couldn't use it for 10 minutes before it crashed until I started deleting some things off my hard drive.  Since then it hasn't happened.  So apparently it has to do with my hard drive being more than 3/4 full or so.

---

### Post by finito on 2008-07-31
I would bet on that too. clear some space on your hard drive.

I find deleting/moving/copying big Folder with terminal is much faster and less buggy.

Just saw your youtube video. Did you try a cold boot after the error.
does it give the same error. 

run a chkdisk utility on your harddrive I don't know how u can do that on ubuntu though. googling reveals 'e2fsk'

---

### Post by LuserName on 2008-07-31
Yes, after a cold boot everything would be normal except that after a few minutes it would crash again.

I tried to use the check function in Gnome Partition Editor, but I think I need to unmount the partition first and I'm not sure how I'd do that.  I could probably do it by booting from my live cd, but I don't think I even have GPE on it, so I'm not sure.  Can anyone help with that?

---

### Post by Sef on 2008-07-31
You can download [GParted]("http://gparted.sourceforge.net/"), and use that.

---

### Post by LuserName on 2008-07-31
Tried the check tool in GParted, but I think it's just fsck.  I need a utility that can check for bad sectors in the disk, not corruption of the file system.  I'll google.  Thanks for the help so far guys.

---

### Post by finito on 2008-08-01
Yup after a good nights rest and a fresh mind here you go..

[http://ubuntuforums.org/showthread.php?t=315126](http://ubuntuforums.org/showthread.php?t=315126)

---

### Post by LuserName on 2008-08-11
Grrrrrrr.  Installed Hardy on my new HDD, and I'm having the same (or similar problems).  What the heck could be causing this?

---

### Post by LuserName on 2008-08-12
Bump

Edit: Well here's some more info about what has happened.

I had firefox and pidgin open.  I went to watch a video in firefox and had no sound, so I double clicked on the volume control to open it up, but all I got was a blank box, so I closed that (had to force quit) and tried to open it from System -> Preferences -> Sound.  As soon as I clicked on Sound, the panels (top and bottom) froze except for the system tray part.  The pidgin icon still turns orange when I get a message.  I can still use Firefox and Pidgin by alt tabbing between them, but soon everything will probably freeze completely and I'll have to restart.

Update: Pidgin crashed, firefox still working.  I'm gonna restart.

---

