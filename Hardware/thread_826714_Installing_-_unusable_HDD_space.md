---
title: "Installing - unusable HDD space"
date: 2008-06-12
forum: Hardware
---

### Post by blueparukia on 2008-06-12
I'm sure this is something to do with my partition setup, but I currently have ~100GB of free space that is unusable when I am trying to install :(

So I probably need to resize a few partitions - any help shall be appreciated.

[img]http://ubuntuforums.org/attachment.php?attachmentid=73780&stc=1&d=1213264592[/img]


Thanks a lot,

BP

---

### Post by housam on 2008-06-12
Boot from ubuntu live cd and go for system >> admin. >> partition editor ( Gparted ) and post the image of your partition table ( by taking a screen shot ).
Also open the terminal ( application >> accessories >> terminal  ) and write the following code :
```
sudo fdisk -l 
```
where -l is the lower case of L , and post the results.

---

### Post by sdennie on 2008-06-12
I think the problem is that you can only have 4 Primary partitions.  You'll have to either push that free space into an existing partition or delete a partition to create some Logical/Extended partitions.

---

