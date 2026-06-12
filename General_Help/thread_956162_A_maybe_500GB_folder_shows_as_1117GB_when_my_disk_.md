---
title: "A maybe 500GB folder shows as 1117GB when my disk is only 1000GB....?"
date: 2008-10-22
forum: General Help
---

### Post by wulfhound on 2008-10-22
Umm, weird problem.

I went to copy a folder off my 1TB drive, to my 600GB partition. Imagine my surprise when I copied the folder and the size was reported to be 1117GB, therefore not enough room to copy it.

My drive that that folder is on is only 1000GB.

I just installed Hardy a few days ago. Is this something to be very, very concerned about? What steps can I take now?

L

---

### Post by chrisamiller on 2008-10-22
What happens when you cd to that folder, then type "du -ch"?

It should scroll a list of folders and sizes past and then give you a total size at the end.  Is that number accurate?  If so, you should be able to do the copy from the command line.

---

### Post by jespdj on 2008-10-23
This is most likely because of this known bug: [bug #220177](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/220177)

It doesn't cause any real problems, so you don't really need to be concerned or do anything about it.

---

### Post by Shazaam on 2008-10-23
As jespdj said just an annoyance. For a work around, open Disk Usage Analyzer and uncheck gvfs-fuse-daemon (Edit>Preferences).

---

### Post by wulfhound on 2008-10-23
> **jespdj said:**
> This is most likely because of this known bug: [bug #220177](https://bugs.launchpad.net/ubuntu/+source/gnome-utils/+bug/220177)

It doesn't cause any real problems, so you don't really need to be concerned or do anything about it.

The main issue is that I can't copy/paste my files because of the size difference. I will look into the workaround posted and see if that helps.

Thanks!

---

### Post by wulfhound on 2008-10-23
> **chrisamiller said:**
> What happens when you cd to that folder, then type "du -ch"?

It should scroll a list of folders and sizes past and then give you a total size at the end.  Is that number accurate?  If so, you should be able to do the copy from the command line.

Yes, that worked, I will try to copy from the command line now. Thank you!

---

### Post by wulfhound on 2008-10-24
I turned off the disk analyzer (unchecked) all drives that have the problem and restarted - but it still is doing this. It's making it really difficult. Does anyone know if there is another fix that would work? I doubt there is but I had to ask.

---

