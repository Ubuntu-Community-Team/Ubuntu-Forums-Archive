---
title: "Help with A New Hardrive"
date: 2006-02-07
forum: Hardware &amp; Laptops
---

### Post by the_beer_chef on 2006-02-07
Ok....have had the OS for a few days now and am slowly getting everything tweaked.  Right now I have a dual boot hardrive "/dev/hda/" with Windows on one side of the fence and Ubuntu on the other.  We'll see if I ever go back to Windows...So far no reason to go back to the dark side.

Anyway I have an additional harddrive /dev/hdb1 that I would like to mount in an easy place to store music, pics etc... Trouble is through searching and looking at the manual and forums I am still having trouble mounting the drive to see it and copy things to it (for Ubuntu). I have been in and out of the "fstab/etc" file tried to "mount" it in the terminal and tried to Enable it in the gpart.  I can't ever get it to work. 

How do I:

1. Mount my /dev/hdb1/ it for general use in Ubuntu? BTW it says in Gpart that it is formatted as ext2 right now.  Which format to use for Ubuntu?
2. a good place that I can see it? 

I know it's not hard I am just not literate in linux enough to know the commands and how this works....Still in that learning a foreign language in a new country thing...

Thanks

---

### Post by taurus on 2006-02-07
If you want to share (write to) that second harddrive between Ubuntu and Windows, than you better format it as fat32 (or vfat).  Assuming that you have, then run

sudo mkdir /mnt/second
sudo mount -t vfat /dev/hdb1 /media/second

Otherwise, should format it as ext3 if you intend to use it with Ubuntu only since it's much format (journal)...

sudo mount -t ext3 /dev/hdb1 /media/second

---

### Post by the_beer_chef on 2006-02-07
Thanks worked like a charm... The drive is for Ubuntu only, the hell with Windows! I knew it was something about my syntax on my commands....

The learning continues....:)

---

### Post by taurus on 2006-02-08
[QUOTE=the_beer_chef]the hell with Windows![/QUOTE]
Good answer...  Just so you know, the learning never stops!  ;)

---

