---
title: "[SOLVED] disappeared files?"
date: 2008-05-16
forum: Hardware
---

### Post by GordSellar on 2008-05-16
I've just upgraded to Hardy from... er, okay, it was 6.06, but it was a clean install. I have four external hard drives, and three of them are working perfectly now -- way better than they were in my previous installation. 

But one 500 MB drive has become very weird. It's formatted to ext3, about half full. The vast majority of the contents, though, are invisible when the drive automounts in Hardy. 

However, the files are there: they're accessible in older installations, as well as in the Linux Mint install on my other laptop. 

Short of copying all my files over from one drive to another via the other laptop, what can I do to try get those files accessible in Hardy? And what's the wisest filesystem choice for a set of external drives? I'll be tidying and re-sorting and would like to do it in the best way possible in terms of stability, recoverability, and compatibility to Ubuntu.

Thanks for any advice or ideas you can offer!

---

### Post by GordSellar on 2008-05-16
Whoops, just posting this to subscribe to my own post! (Missed that in the first post.)

---

### Post by GordSellar on 2008-05-16
Aha! It seems I solved it myself. 

When I plugged the drive in on an installation of Linux Mint, the full contents of the folder were visible, including a couple of files that had somehow gotten messed up, and wouldn't allow me to delete or move them. 

Once I deleted those (using the command line as root) I found that the drive mounted normally in Hardy. Still going to move all the files to another (freshly formatted) drive -- not sure which format to choose, but I will research it.

---

### Post by psavva on 2008-05-16
Mark it as solved

---

### Post by GordSellar on 2008-05-16
Ooops!
Thanks for the reminder, Psawa!

---

