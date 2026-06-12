---
title: "Rhythmbox can't access remote files?"
date: 2008-11-11
forum: General Help
---

### Post by HalPomeranz on 2008-11-11
I've recently installed 8.10 and for the most part things are working extremely well.  The one difficulty I am having is accessing my music files from my network file server using Rhythmbox.

This used to work fine for me under Hardy.  I would mount the file system where my music lives via the "Places... Connect to server..." (it's on an SMB share from a Samba server elsewhere on my network).  Then I would fire up Rhythmbox and that would cause a little pop-up asking if I wanted to allow Rhythmbox to be able to access the file system.  Once I confirmed that, I could access the files and play my music.

Under Ibex, I can mount the file system and browse it with File Manager.  I can even click on individual music files and play them.  But when I fire up Rhythmbox, I don't get the dialog about allowing Rhythmbox to access the remote file system and Rhythmbox is unable to read any of the music files to play them.

I'm sure this is just due to something trivial, but I can't figure out what it is.  I've searched the Forums a bit without luck.  Any help would be appreciated.  Thanks!

---

### Post by HalPomeranz on 2008-11-12
Bump.

---

### Post by afl on 2008-11-12
filesharing with foreign hosts under Samba is definitively broke on Ubuntu 8.10. There are a couple of threads about it, but it does not look as if that will be fixed soon :(

---

### Post by HalPomeranz on 2008-11-12
Thanks for the news, afl.  Can you point me at a the threads where this is being discussed (if you have them handy)?  Thanks!

---

