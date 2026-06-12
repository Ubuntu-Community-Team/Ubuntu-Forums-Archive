---
title: "Gparted did strange things at resizing my partitions :("
date: 2009-12-06
forum: Hardware
---

### Post by casidiablo on 2009-12-06
Hi guys... 
 
I'm in a serious trouble because Gparted didn't do its work as expected. I had two partitions on my disk: first one with ext4 and the second one with ext3. I deleted the first partition since I won't need it anymore, and then I was going to resize the ext3 partition to fill all the space that was empty. But, once Gparted "finished" resizing that partition, I got a huge etx4 partition with all data that the deleted partition had, and with out the data of my ext3 partition... [IMG]http://forums.gentoo.org/images/smiles/icon_sad.gif[/IMG] 
 
is there any way I could fix such a big and weird problem? 
 
Thanks for reading!

---

### Post by ibuclaw on 2009-12-06
> **casidiablo said:**
> Hi guys... 
 
I'm in a serious trouble because Gparted didn't do its work as expected. I had two partitions on my disk: first one with ext4 and the second one with ext3. I deleted the first partition since I won't need it anymore, and then I was going to resize the ext3 partition to fill all the space that was empty. But, once Gparted "finished" resizing that partition, I got a huge etx4 partition with all data that the deleted partition had, and with out the data of my ext3 partition... [IMG]http://forums.gentoo.org/images/smiles/icon_sad.gif[/IMG] 
 
is there any way I could fix such a big and weird problem? 
 
Thanks for reading!

You probably got the two partitions confused. No use blaming the software here.

But since you got yourself into this situation, install **testdisk**
```
sudo apt-get install testdisk
```
And fire it up - you should be able to scan the drive for lost partitions and be able to recover as much of the **absolutely needed** sensitive information as you can.

Best guide I know for it is here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Follow the steps in that guide, and when you select **Deeper Search**, wait for it to finish, then select the partitions that **used** to be there before the edit with gparted using the Left and Right arrow keys to highlight them. (This is loosely documented in the guide).

Then Write it to recover the partition table. You may need to reboot into the LiveCD again, then check to see what data of the ext3 partition can be backed up.

Regards
Iain

---

### Post by casidiablo on 2009-12-06
Thank you so much... I'll try to do it...

---

