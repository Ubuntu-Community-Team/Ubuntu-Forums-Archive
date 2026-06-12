---
title: "Removing Ubuntu from external harddrive"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by Xovan on 2007-07-22
I'm a nub a linux no doubts about that.

I want to remove ubuntu from my external harddrive and turn it back into something windows xp can use.  But the external harddrive no longer appears in windows in my computer.  Ubuntu never really worked well on this external drive (far too many errors and problems just installing it) so I'd like to wipe the whole drive clean and turn it back to ntfs.  How do I do that?  Thank you for any information you can provide.

---

### Post by floke on 2007-07-22
Windows can't recognise Linux filesystems (good eh?). Best bet is to load up a LiveCD; plug the external in; get it mounted; then use Gpartewd to delete the ubuntu partition and reformat the space as NTFS or something. You should only do this if the MBR for booting the external drive was on the drive itself - i.e. not on your internal hard drive,

---

### Post by Xovan on 2007-07-22
Thanks for the snappy reply.

I guess I have 2 things on my to do list.

-fix mbr using another tutorial I found

-use Gpartewd to delete the ubuntu partition and reformat the space as NTFS

Is there any other things I'll need to do or will I be good from there?

---

### Post by Xovan on 2007-07-22
It won't let me touch the linux partition with the mbr on it in gparted.  I was able to delete the swap partition and reclaim it for ntfs but the bulk of linux is still in there.  Where do I go from here?  What do I do to unlock the linux partition with the mbr to reclaim the disk?

Wait nvm I had to unmount the partition.  Noobie me.

---

