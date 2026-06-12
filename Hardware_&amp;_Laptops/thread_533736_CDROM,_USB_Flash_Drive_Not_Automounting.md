---
title: "CDROM, USB Flash Drive Not Automounting"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by Greslore on 2007-08-24
I am using Kubuntu 7.04.  After doing a search, I see a good amount of posts in regards to people seeming to have the same issue, but nothing in the way of a good fix.

Problem: Dell 745 not automounting CDs, USB Flash Drives.  It did work when system was first installed about 1 month ago.  System has a DVD-ROM, and a DVD-RW Drive.  I went to install an app this morning off a CD, and no automounting.  Perhaps an apt-get update; upgrade broke something?

Has anyone found a good fix for this?

EDIT: I could do a wipe and reinstall of Kubuntu 7.04, but would this fix the problem?  I am afraid that after updating the packages it would just break automounting again.

---

### Post by Greslore on 2007-08-24
Update: I just had a CD in the DVD-ROM prior to rebooting.  Upon the reboot, I was able to see the cd contents under /media/cdrom0 and under "Storage Media" > "cdrom0".  But no desktop icon for the loaded cd.  I umounted via "umount /media/cdrom0".  

Ejected, reinserted.  Again, no automount.  But I did a "mount /media/cdrom" and it was available under /media/cdrom0.  While I can see the contents by going to media/cdrom0 via konsole or konqueror, I can NOT see the contents by clicking on "Storage Media" > "cdrom0".

Ideally I need this to work with an automounted icon upon inserting cd/usb key on the desktop.  Its a machine that is going to be used by a good amount of people with very little computer skills.  I am really tempted to just reformat and reinstall.  It would mean re-doing alot of work, but if it fixes the problem, then its worth it.  Again though, I am not sure of the cause of this automount not working so am afraid to do all that.  :confused:

---

### Post by Greslore on 2007-08-24
I suppose I could also just go back and reformat everything to Dapper 6.06?  Anyone know if that version is affected by this automount issue that so many seem to be having??

---

### Post by Greslore on 2007-08-24
Alrighty, I think I found an acceptable workaround for this so far... 

On the KDE desktop, I created a direct link on the desktop to open up both CD/DVD ROM devices.  Works good.  Now I only need a way to create a link on the desktop to any USB Flash drive that a user can plug in.  



(In retrospect, I should of not of kept replying to myself, and should of just made edits to the original post.  My apologies for the thread spam)

---

