---
title: "Can't use functions at Gparted"
date: 2008-08-28
forum: General Help
---

### Post by david sousa on 2008-08-28
Hello, i installed gparted but i can't use its functions. It seams like it is read only, because i can't click them.

What can i do?

---

### Post by Too Late on 2008-08-28
Are you having the "key" symbol (or lock if you're using an older verion of gparted) next to the partition(s)? If so, that means that the partition is mounted. You can't modify a mounted partition. You can try to unmount them by right-clicking and select 'umount'. If that doesn't work (i.e. you try to modify your root partition), you should use the LiveCD instead.

And of course, did you start the program with gksudo? (I don't know if it even starts without the proper permissions.)

---

### Post by david sousa on 2008-08-28
Yes i have that "key". but what happens if i click unmount? Will i loose something?

---

### Post by plasmafusion on 2008-08-28
run "sudo umount -a"
it'll unmount any filesystems that can be unmounted. you won't lose any data but if, like Too Late said, the device is reported as busy then you'll need to use the live cd..
remount them with "sudo mount -a"

---

### Post by Too Late on 2008-08-28
What is your goal? I mean, what are you going to do to those partitions? Unmounting doesn't do any harm, it just simply "ejects" that partition from your system so that you can't use it until you mount it back. At the latest, next reboot will mount that. But modifying partitions can cause much harm, so you have to do what you're doing.

---

### Post by david sousa on 2008-08-28
I want to create a new one with some instructions that i saw there at google. But if i unmount it am i going to be able do modify it without broke it? Do i have to mount it again before the reboot? Does the creation of a new partition formats the original?

---

### Post by ad_267 on 2008-08-28
> **david sousa said:**
> I want to create a new one with some instructions that i saw there at google. But if i unmount it am i going to be able do modify it without broke it? Do i have to mount it again before the reboot? Does the creation of a new partition formats the original?

Resizing a partition doesn't involve reformatting, you can just shrink it with gparted. But first it has to be unmounted. If it is your root partition you have to boot from the live CD to do this. You don't mount it again, it will be automatically mounted when you boot.

---

