---
title: "Construct a RAMdisk"
date: 2012-04-20
forum: Hardware
---

### Post by Groggster on 2012-04-20
Hello! I would like to construct a RAMdisk using the ext4 filesystem, how do I go about doing that? Say for instance that I want a RAMdisk mounted in /mnt/ramdisk which is using ext4 as its file system and has a storage capacity of 2 GB.

---

### Post by SlugSlug on 2012-04-20
there is already a ram disk

/dev/shm

or 

/dev/run ?

its 1/2 the size of your total ram

---

### Post by Groggster on 2012-04-20
Okay, so how do i format them to ext4? It seems that /dev/shm is already mounted.
none /dev/shm tmpfs rw,nosuid,nodev,relatime 0 0

I can't find the other one in /dev though i do have ram0 through ram15. Can i use them?

---

### Post by SlugSlug on 2012-04-20
AFAIK you can't 'format' it,

it uses tmpfs 


/dev/shm  is correct - just cpoy files to it or what ever u wanted to do 


(all will be lost on a reboot just incase u didnt know :)  )

---

### Post by Groggster on 2012-04-20
Damn, so i can not have a ext4 RAMdisk? Yes, i am aware that the storage is highly volatile. Even if i for instance umount the /dev/shm then do a mkfs.ext4 /dev/shm or something?

---

