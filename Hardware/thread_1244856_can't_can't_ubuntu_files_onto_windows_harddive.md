---
title: "can't can't ubuntu files onto windows harddive"
date: 2009-08-19
forum: Hardware
---

### Post by cactusfrog on 2009-08-19
Can't transfer files onto windows harddive (sorry about the title typo can't edit it) 

My windows XP laptop got a really nasty virus that corrupted ever exe. Unable to boot up windows i took the harddive out of my laptop and put it into my desktop running ubuntu 9.04. i then copies all my documents of my windows harddive an onto to ubuntu harddive. After i fixed my computer i tried to put the files back on to my windows harddive but although in ubuntu it displays the files when using windows it does not. What should i do so that i can see these files on my windows harddive. BTW i don't have any external harddive to transfer over the data.

---

### Post by lisati on 2009-08-19
One possible explanation is that Windows and Ubuntu use different file systems.

Within Ubuntu you might need to install something like ntfs-3g (via applications->Add/remove software) to enable ntfs suppoer.

There are add-ons for Windows that let you access ext3 partitions (as used by ubuntu)

---

