---
title: "Disk drive won't run/copy DVD or ROM. input/output problem"
date: 2018-03-15
forum: Hardware
---

### Post by amon+ on 2018-03-15
I rarely use my disk drive at all. So it has been years since I've used it. I can't even remember when i had last. But now when i put in a DVD (most dvds, i did get one from the local library, learn physics, to run, but vlc showed errors about not being able to set the title) or a ROM disk, it won't run. It loads the disk and i can view the files in the file window. But if i press play in vlc it tries for a split-second and does nothing. If i try to copy a file off the disk i get this "Error splicing file: Input/output error" Some sources tell me it could be a damaged disk (which is why i tried random disks at the library) i haven't had a brand new disk to try but i've tried some pretty clean looking disks with the same result.

I have libdvdread4 and libdvdcss2 and i've used regionset to make sure i was set to 1 (US). These are all the solutions i could find people mentioning and it's not working. If there is some kind of diagnostic tool that can test the drive it's self, i can't find it. But the drive does work for audio cds and for that low budget learn physics dvd. I tried swapping out the drive with the one from my last laptop (both HP) but had the same issue.

Since people will probably ask i have ubuntu 16.04 LTS (32-bit) with intel celeron processor. I don't know why people ask since they never seem to give a follow up response when people give those details.

---

### Post by TheFu on 2018-03-16
You could try using **vobcopy** to make a local copy to watch, but since you don't use a disk drive, where would  you store it?


    > I rarely use my disk drive at all. So it has been years since I've used it. I can't even remember when i had last. 
Hopefully, you really mean DVD drive, not disk drive.

---

### Post by amon+ on 2018-04-16
Yeah i can't make a copy of a disk without a working drive. and it's not just DVD s the drive is also used for Software ROMs and audio CDs.

Anyhow i still haven't found any solution to this issue.

---

### Post by TheFu on 2018-04-16
So vobcopy didn't work? Any errors that can be copy/pasted here?

---

