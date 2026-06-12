---
title: "GParted + External HD"
date: 2008-11-07
forum: General Help
---

### Post by chuuk on 2008-11-07
I recently purchased an external HD and it came with some manufacturer provided files written using the NTFS filesystem - I rushed along with GParted and formatted it to Ext3. 

The problem with that was that I then kept having to open nautilus with admin privileges in order to edit any files on the disk, which meant that I had to keep opening it through terminal to do the most basic of tasks. If I opened it without using gksudo "nautilus" it wouldn't allow me to complete the task, saying I didn't have sufficient permission.

I reformatted it into the FAT32 system, it's working fine.

Clues anyone?
I would like to go back to the Ext3 system as soon as possible.

---

### Post by cdtech on 2008-11-07
When formatting a USB drive the top level is "root". Any folders can be created by "users" under the top level and will be owned by that user. If you create a user folder or just a folder while under a user account that folder will be the owner of that user and you can place your files within that folder.

Hope this helps ya......

---

