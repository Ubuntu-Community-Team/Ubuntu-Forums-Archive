---
title: "Partition size not accurate after restoring backup with partimage"
date: 2008-05-13
forum: Hardware
---

### Post by PvtJohnson on 2008-05-13
I was running low on space on my ubuntu partition so I decided to shrink down an NTFS partition that I use for storage. I used partimage along with a live cd to create the backup, then deleted the entire linux partition with gparted(I figured it would be a quick fix since I didn't have an hour to resize the partition), shrunk the NTFS partition, created a new ext3 partition, and then restored with partimage.

Everything worked flawlessly, but when installing apps it still says that I have 1gb remaining when I should have 20gb free. The filesystem properties also tells me that I have only 1gb remaining. 

When I pull up terminal and run "sudo fdisk -l" it lists the partition with the correct size. Is this a common bug when restoring with partimage? I have searched and searched and couldn't find anything. It doesn't affect the way the system works now, but I'm worried I might get into trouble when that 1gb is filled up.

I have been using linux for about six months and lurking this forum for about just as long, finally an issue I can't solve with google so I get to post, w00t. I love this place!!

---

