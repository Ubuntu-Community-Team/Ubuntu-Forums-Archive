---
title: "How do I do a surface scan?"
date: 2008-12-14
forum: Hardware
---

### Post by sternkanz on 2008-12-14
In windows I know I just do checkdisk... is there an easy way to do this in ubuntu?

Please consider me a total n00b in regard to this... someone recommended smartctl but I have no idea how to use it and the gui for it needs to be .configure/make/make installed whatever that means.

If anyone can help I'm very grateful thanks!

---

### Post by tgalati4 on 2008-12-14
sudo apt-get install badblocks
sudo badblocks /dev/sda


Go for a walk.

---

### Post by sternkanz on 2008-12-16
thank you!

---

### Post by doobiest on 2008-12-16
fsck.ext3 -c will check for bad blocks. this is built in so you dont need to install anything.

if it's not and ext3 filesystem, from a terminal type 'fsck.' then hit tab. It will pull up a list of supported filesystems:

doobiest@LinuxBox:/etc/apache2$ fsck.
fsck.cramfs    fsck.ext2      fsck.ext3      fsck.ext4      fsck.ext4dev   fsck.minix     fsck.msdos     fsck.nfs       fsck.reiserfs  fsck.vfat

---

### Post by miros84 on 2008-12-16
I cannot find where to go to put new messege. I mean new post.

---

### Post by sternkanz on 2009-06-04
> **tgalati4 said:**
> sudo apt-get install badblocks
sudo badblocks /dev/sda


Go for a walk.

Sorry to dredge up an old post, I never got around to doing this unfortunately but now I once again have my hands on the PC with the problem and when I put in:

sudo badblocks /dev/sda

it just sits there until I press Ctrl+C. Will it show me the results eventually? It just didn't seem like it was doing anything.

---

### Post by doobiest on 2009-06-04
> **sternkanz said:**
> Sorry to dredge up an old post, I never got around to doing this unfortunately but now I once again have my hands on the PC with the problem and when I put in:

sudo badblocks /dev/sda

it just sits there until I press Ctrl+C. Will it show me the results eventually? It just didn't seem like it was doing anything.

I would recommend you follow my previous post. That should do it, and if you did that and it didnt do it, let me know.

---

