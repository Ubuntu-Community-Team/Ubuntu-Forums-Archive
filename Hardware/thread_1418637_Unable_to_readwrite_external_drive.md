---
title: "Unable to read/write external drive"
date: 2010-02-28
forum: Hardware
---

### Post by shane wiley on 2010-02-28
Problem with read/write.
I have a small MP3 player connected to my laptop via a usb. The player  appears to be formatted FAT32.  It is recognised  by Ubuntu (Koala) and first I was able to download files to it from my laptop(s), but lately it is 'frozen', I can copy files out but cannot delete/add/rename. I am logged in as administrator, and should have read/write of everything. 
If if go to Windows (I have a dual boot system) then there is no problem, can read and write to the MP3 player even tho I am not logged in as windows administrator.
(PS:keep any replies simple as possible, am still in a windows mindset)

Shane Wiley
[email]ozwileys@gmail.com[/email]

---

### Post by karatedog on 2010-02-28
for a starter, put the result back here:
```
fdisk -l
```
(with the media player attached)

It is possible that the automount feature mounts the device the wrong way.

---

