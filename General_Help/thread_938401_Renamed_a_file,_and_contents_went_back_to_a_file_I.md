---
title: "Renamed a file, and contents went back to a file I deleted previously!"
date: 2008-10-04
forum: General Help
---

### Post by SlaughterDog on 2008-10-04
(I put this under "all variants" because I figure it's just a Linux question). 

I saved a text file to my home folder. I renamed the backup copy that gedit made, and suddenly, the contents went back to a text file I had deleted a while ago!

Can someone explain why this happened, and how to prevent it from happening again? I don't really know anything about how Linux manages files. I know (or think I know) that when you delete a file, just the 'table of contents' entry on the disk gets removed, but can someone explain this a but further?

---

### Post by jamesrl on 2008-10-05
This has nothing to do with how ext2/ext3 partitions work, it has to do with how gedit (and similar editors like say nano) work by default.  
Let's go through an example:  you write a file called mytext.txt that contains the text: "first draft" and save it.  On your hard drive you have a file called 
mytext.txt  containing the text "first draft".

You then edit this file, and change "first draft" to "second draft", when you save this, what gedit does is it saves "first draft" to mytext.txt~ and "second draft" to mytext.txt.  If you repeat this again with a "third draft" saved to mytext.txt, then mytext.txt~ will be "second draft".

It seems you decided to move mytext.txt~ to mytext.txt, which overwrote the original file.

This feature is  guided by a setting in gedit by Edit->Preferences->Editor->Create a backup copy of files before saving.

---

### Post by jamesrl on 2008-10-05
Also, in general you are basically correct in that normally when you delete a file, you don't overwrite the contents of that file.  However, this is the same in windows, as it doesn't make sense to overwrite a file's contents when you are deleting it (instead of just deleting the pointer of where on the hard drive to look for the data contained in that file).  In linux if you really want to get rid of information you can use the shred command to overwrite the file with data.

---

### Post by SlaughterDog on 2008-10-05
jamesrl, you hit the nail on the head. I knew that gedit did this, and after posting this thread, I realized that gedit doesn't save two copies on the first save, so the old one was there all along.

---

