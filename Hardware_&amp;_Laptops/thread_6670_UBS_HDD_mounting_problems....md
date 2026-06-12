---
title: "UBS HDD mounting problems..."
date: 2004-11-30
forum: Hardware &amp; Laptops
---

### Post by jeremymarx on 2004-11-30
Just recieved my cd in the mail yesterday, and played with the LiveCD to see if I would want to use ubuntu.  I loved it!  However I could not see my USB HDD with the CD.  I thought it was just a problem with the Live.  Blew my old dist away, and installed ubuntu.  Now don't get me wrong here.  I am very pleased with "Warty", and have no intention of ever going back, but I still can't see the contents of my drive.  And I was able to with Suse 9.2.  It is a Maxtor 120 Gig with NTFS on it.  The error I am getting from Gnome is:
It shows itself as usb0
Double click on it and this is what I get:
[B]Mount Error:
Unable to mount the selected volume.
mount: I could not determine the filesystem type, and none was specified[/B]
There are files on this drive that I would love to have access too, so if anyone can help I would appreciate it!

-Jeremy Marx

---

### Post by captfats on 2004-11-30
Excuse me if I"m wrong on this but the ntfs kernel module is not loaded. 

so this should work 

sudo /sbin/modprobe ntfs

then mount your drive. 

Worked for me

-Mike

---

