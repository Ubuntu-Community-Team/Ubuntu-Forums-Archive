---
title: "Problems ripping data CD in Ubuntu"
date: 2008-09-06
forum: General Help
---

### Post by Aug Leopold on 2008-09-06
I have been trying to rip several data CDs in Ubuntu as ISO images. However, whenever I complete the rips and look inside the images with archive manager all of the files get ;1 appended to them. (ex. example.txt becomes example.txt;1) This happens to every file on the CD, and although it isn't a fatal error it is really quite annoying. I have already tried several different disks, so the media is not the problem and I have also tried using both K3b and Brasero to rip the images with the same result from both programs. Anybody have an idea as to what might cause this and how to fix it?

---

### Post by kostkon on 2008-09-06
> **Aug Leopold said:**
> I have been trying to rip several data CDs in Ubuntu as ISO images. However, whenever I complete the rips and look inside the images with archive manager all of the files get ;1 appended to them. (ex. example.txt becomes example.txt;1) This happens to every file on the CD, and although it isn't a fatal error it is really quite annoying. I have already tried several different disks, so the media is not the problem and I have also tried using both K3b and Brasero to rip the images with the same result from both programs. Anybody have an idea as to what might cause this and how to fix it?
I think the problem lies with the archive manager. So, don't worry, your ISOs are just fine.

---

### Post by Aug Leopold on 2008-09-07
Wow, you were dead-on with this one. I installed IsoBuster via Wine to check this out, and sure enough the file names turned out fine when viewed through that. I wonder why this only seems to happen with archive manager on ISO images I've ripped under Linux and not others. If could explain why this happens, I'd really like to hear it, but otherwise thank you for your help.

---

### Post by kostkon on 2008-09-12
> **Aug Leopold said:**
> Wow, you were dead-on with this one. I installed IsoBuster via Wine to check this out, and sure enough the file names turned out fine when viewed through that. I wonder why this only seems to happen with archive manager on ISO images I've ripped under Linux and not others. If could explain why this happens, I'd really like to hear it, but otherwise thank you for your help.
It is a known bug of *File-Roller* (that is the name of the default archive manager in *Ubuntu*). Here is [the bug report]("https://bugs.launchpad.net/fileroller/+bug/110942"). It happens, unfortunately, for any ISO image, not only for the ones made under *Ubuntu*.

---

