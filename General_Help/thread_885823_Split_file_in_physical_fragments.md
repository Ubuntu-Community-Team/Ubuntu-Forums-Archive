---
title: "Split file in physical fragments"
date: 2008-08-10
forum: General Help
---

### Post by bulgarion on 2008-08-10
Hi guys/gals, I know this isn't a "straightly-ubuntu" question, but that's my problem: I have a FAT32 partition, and I need to put on that filesystem a file which is >4G. The fact is that I need the applications using it to see it as a single file...
Example: AVI file of 5.8 GB named "greatmovie.avi", if I load it with, say, VLC I shall be able to see the movie, but on the filesystem I have something like greatmovie.avi.001 (size 1G),  greatmovie.avi.002 (size 1G), and so on.
Is there something that can do this? 
Sorry for the really ppor explaination!

---

### Post by jocko on 2008-08-10
I don't think splitting the file will be a problem (I don't know how, but I'm sure some video editing tool would do it).
Having a media player handling the parts as one single file sounds more difficult. Wouldn't it be just as well to make a playlist instead, so the media player plays the parts one after the other?

---

