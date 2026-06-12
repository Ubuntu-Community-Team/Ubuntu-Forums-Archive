---
title: "How do I mount a windows fat32 drive in ubuntu?"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by ekravche on 2005-08-01
Hello,

I'm trying to mount a windows fat32 drive in ubuntu, but I'm unsure how to do it. 

Please help.

---

### Post by hod139 on 2005-08-01
[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

---

### Post by dave9191 on 2005-08-01
There is one thing that I really don't get. Some questions come up time and time again. Thats why people give up a lot of their time and wright how to's and there are so many forum threads about this already. A simple google search, or a search of the forums or a browse throught wiki will answer the question in the matter of seconds, as opposed to posting a new thread and waiting an unspesified amount of time for a reply. 

[Ubuntu FAQ - mounting windows FAT32 and NTFS](http://www.ubuntuguide.org/#windows) 

[Google Search Results](http://www.google.com/search?q=mount+fat32+ubuntu+&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official) 


Dave

---

### Post by ekravche on 2005-08-01
Got it thanx a lot! It was very easy to mount.

---

### Post by ekravche on 2007-01-04
All you need to do is add this line. Seems to work for me

# /dev/hdd1 -- converted during upgrade to edgy
UUID=2D2B-1C0D /media/windows vfat iocharset=utf8,umask=000 0 0

Edgy seems to pick it up anyway, without any human intervention

---

### Post by raul_ on 2007-01-04
Err...why this post?  And I don't think your drive's UUID would work in other user's systems...after all...they are UUID :rolleyes: Universally Unique Identifier

But again, why answear to a post dated of 2005, which has already been answered, and created by you in the first place? :mrgreen:

---

