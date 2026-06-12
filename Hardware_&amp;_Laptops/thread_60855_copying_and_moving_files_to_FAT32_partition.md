---
title: "copying and moving files to FAT32 partition"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by tonysathre on 2005-08-29
i have a 60 gb hdd which has M$ XP on it on hda1, i have an 8.6 gb with kubuntu on it on hdb1...  on hda5 i have a 4 gb FAT32 partition to share files back and forth.  in linux when i try and drag and drop files on the FAT32 partition i get a permission error and wont let me, but when i use the command line i also get an error but the files copy anyway, why does this happen and how can i fix it so i can drag and drop instead on using the terminal.

---

### Post by c0rderr0y on 2005-08-29
can you post your fstab?

---

### Post by tonysathre on 2005-08-30
im not at my linux box right now but i will post it tomorrow

---

### Post by Kremlin on 2005-08-30
I'm in a similar situation to yours, so I'll show you what I did.

Here's my fstab entry:

/dev/hda5       /mnt/share      vfat    defaults,umask=0002,gid=109     0      0

Okay, so first up the umask. This tells linux to mount the drive with full permissions for owner (root) and group, and read/execute permissions for everyone else.

The gid is set to 109, which happens to be the admin group of which my user is a member. Thus, admins can write to the share. You can change the gid correspondingly to whatever you want (eg gid=100 for all users) or create your own new group in /etc/group to add users to. My needs aren't that complex, since I'm the only user of this box.

That's all there is to it, really. Replace the block device and mount point with the relevant ones for yourself, and you should be good to go.

If your fstab already looks like this, then the issue is something else, so try this first then get back to us.

---

### Post by tonysathre on 2005-08-30
k thanks, ill try it as soon as i get home

---

### Post by tonysathre on 2005-09-01
thanks, ya that was the problem it works now

---

