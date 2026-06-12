---
title: "PSP Bug"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by mikesena on 2006-08-10
Hi,

My PSP's usb does not function correctly.  When I plug my PSP in and turn on USB mode, it is detected by ubuntu and mounted.  I can view and add contents fine.  However, when it comes to deleting, it stuffs up.  If i delete files, the free space is not recovered.  I had a couple of n64 roms which i was testing on daedalus (for those who know it), and needed the 200mb they were taking up.  when i deleted them, my used space dropped, but my freespace stayed the same.  it also appeared on the psp itself as only having the same amount of space as it did, before i deleted all the files.  in other words, apparantly, the size of my psp decreased!  i have a 1gb memory card, which is used as the storage.

However, i recently found a way to fix the problem, sort of.  using the sudo rm command correctly deleted files :S

Why does rm work, the explorer doesn't and how can i fix it so that the explorer does work!

---

### Post by mikesena on 2006-08-10
anybody?

---

### Post by bmichel on 2006-08-10
allow visualization of hidden files on your PSP file system (nautilus > View > Show Hidden Files). You should have an hidden directory (.Trash-xxxx) for Trash that you can remove safely. It happens on FAT32 FS.

---

### Post by mikesena on 2006-08-11
oh really, sweet thanks

---

