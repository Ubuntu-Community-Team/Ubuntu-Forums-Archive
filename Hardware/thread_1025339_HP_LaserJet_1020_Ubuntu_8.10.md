---
title: "HP LaserJet 1020 Ubuntu 8.10"
date: 2008-12-30
forum: Hardware
---

### Post by Zizuph on 2008-12-30
I have an HP 5610v InkJet all-in-one, and an HP 1020 LaserJet plugged into the USB ports of an Ubuntu 8.10 box.  Both printers were working at first, and in fact, worked for a couple of months without a problem.  Recently (and I don't know exactly at what point this began, so I can't be sure if it was an update which caused it) I noticed the 1020 would accept print jobs and clear them, but would no longer actually print anything or make any sounds like it was warming up at all.  Meanwhile, the 5610 continues to function normally, even the fax part of it, which is sweet.  I have been searching for an answer off and on for a while now, and have tried a few things on my own.  I've been printing to pdf and plugging the 1020 into an XP box in order to get my large documents out, but that is getting old quick.

So far, I've tried...
- power cycling the 1020,
- plugging the 1020 into a different usb port,
- testing the 1020 on a Windows XP box using the same usb cord (worked),
- deleting the printer from the list and allowing it to re-detect when I plugged it back into the 8.10 box, &
- changing the USB port assignment in CUPS from the detected "USB FNOSORK" (don't know what that stands for) to "USB #1".

The results are always the same:  Print jobs are accepted and cleared with no print-outs.

Has anyone else experienced this problem with a similar setup and found a solution?

---

### Post by odduntu on 2009-02-02
exactly same for me. but has also problem in XP. Same in 8.04.:(

---

### Post by odduntu on 2009-02-02
I tried to install the

[http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)

it works fine first ... then after power off/on it stops. Delete the printer and add new ... then it works. Not even a good work around. I am a little suspicious ... it can be hardware problem too. Any?

---

### Post by khelben1979 on 2009-02-02
I recommend that you use the printer driver [from this place]("http://foo2zjs.rkkda.com/").

---

### Post by Dipper on 2009-02-12
That page emphatically says not to use the foo2zjs driver from the ubuntu repository. Instead, they want you to download from their site and compile from source.  The page also makes reference to Dapper, Feisty, and Gutsy.  I wonder if the driver in the intrepid repository has been fixed.  Hopefully, because compiling from source does not work half the time.

---

### Post by Sprax on 2009-02-17
[http://ubuntuforums.org/showthread.php?t=1047372&highlight=hp+1020](http://ubuntuforums.org/showthread.php?t=1047372&highlight=hp+1020)

---

