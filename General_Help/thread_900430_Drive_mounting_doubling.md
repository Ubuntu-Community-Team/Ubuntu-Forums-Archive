---
title: "Drive mounting doubling?"
date: 2008-08-25
forum: General Help
---

### Post by mateoc15 on 2008-08-25
I'm having some problems with drive mounting I believe.

I have an NTFS drive with no boot records on it, just a single partition NTFS formatted drive with a bunch of files on it.  I have (I think) mounted it to /media/Data.  So this weekend I went through all of my photos in F-Spot (pretty nice app!) and tagged all of my photos, etc.  All of the thumbnails still appear (stored in the application data I assume in the sql-lite DB file maybe) but I selected a specific tag, selected all photos under it, and then used the export function to try to export all of them to a directory on my desktop.  It failed.  So I selected them all again, right clicked, and used the Copy File Location and pasted it into gedit.  After looking through my directories and setup I found that I have a directory called /media/Data_ (with an underscore).  The file name that was set up in F-Spot was something like /media/Data/Photos/picture.jpg but that file didn't exist when I tried to open it using just the plain photo viewer app.  However, when I opened /media/Data_/Photos/picture.jpg it exists (note the underscore again).

So what's going on here?  I modified the fstab file when I first installed Ubuntu and made sure that it wasn't duplicating any actions (mounting the same directory twice) but maybe that's my problem.  Is it possible that in one place it mounts Data and then tries again, but since it's already done it uses Data_ instead?

Also, mounting these drives is a bit sketchy.  Sometimes I have to reboot for it to recognize the drive immediately on boot (I can always mount it manually with no problems), but other times on reboot it mounts every NTFS drive I have without any manual actions.

Hopefully this is fairly clear.  Let me know if I can give you any more information.  Unfortunately I can't access my desktop from work so if you need any files etc I'll have to give them tonight when I get home.

Thanks in advance!

- Matt

---

### Post by mateoc15 on 2008-08-25
And one more thing.  Assuming I get all of this straightened out is there a good way to access that sql-lite DB file (user interface) so that I can replace all file paths containing Data_ with Data (or however it comes out)?  Is that the easiest way to correct it?  I have plenty of SQL experience in Oracle and MSSQL so writing a script wouldn't be a problem after a bit of research I'm sure.

Thanks so much!

---

### Post by mateoc15 on 2008-08-25
I found [this]("https://bugs.launchpad.net/ubuntu/+bug/212278") but I'm really not sure how to find the solution, if any, and check bug progress.  Is bugs.launchpad.net an "official" bug reporting tool for Ubuntu?  Should I file a bug elsewhere?  Can anyone think of a work-around?

Thanks!

---

