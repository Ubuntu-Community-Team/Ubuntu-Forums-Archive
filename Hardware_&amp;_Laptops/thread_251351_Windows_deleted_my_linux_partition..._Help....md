---
title: "Windows deleted my linux partition... Help..."
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by burk on 2006-09-05
Hello

Some time ago I lived happily with my dual boot system on my 300GB harddrive, with one 100GB primary partition for windows, and one logical partition for linux, and one primary partition for swap. The logical partition consisted of a / partition a /home partition and a fat-partition for sharing files between the two OSes. Then, while using windows (and the windows disk was very full), I decided to use the last free space on my harddrive and make another fat-partition. I did it with XPs builtin partition manager. Then, when trying to reboot the computer, I get grub error 15, described here: [http://forums.gentoo.org/viewtopic.php?t=122656](http://forums.gentoo.org/viewtopic.php?t=122656)

I am now using the liveCD I previously installed Ubuntu from, and when I start GParted, it shows something like this [ATTACH]15330[/ATTACH] The green dot is my old Ubuntu partition and the red dot is the new fat-partition I tried to make. 

What I want to do is to somehow recover the linux partition, because it is obviously there, its just that the computer doesn't see it as one.

---

### Post by Brent Dax on 2006-09-05
> **burk said:**
> What I want to do is to somehow recover the linux partition, because it is obviously there, its just that the computer doesn't see it as one.
You're correct in thinking that the partition's data is probably intact; you just need to recreate its entry in your drive's partition table.

First of all, if you have a spare hard drive that's large enough, make a full image of your drive; that way you won't risk losing data.  You'll want to use the *dd* tool on the Ubuntu LiveCD to do this:

[FONT="Courier New"]dd if=/dev/sda of=(destination file/drive)[/FONT]

Next, simply create a new partition that's exactly the same size and location as the old one.  This should be easy in gparted.  **Make sure you set the formatting option to "Unformatted", or it'll reformat the partition!**

Finally, reboot.  Your partition should now be back; at worst, you may have to adjust your GRUB and fstab settings if the partition numbering changed.

---

### Post by burk on 2006-09-06
Thanks :)

Actually, thats what I though was the best solution too after googling, but I thought it was hard to create a partition without formatting it.

I have now started the liveCD but cannot find any formatting options, does it ask me when I click apply? (I do not dare to test it to find out)

---

### Post by Brent Dax on 2006-09-06
It shouldn't be that difficult with gparted--see this screenshot:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=15411&stc=1&d=1157580024[/IMG]

It should definitely be possible to only grab the unformatted area with dd--you'd just have to use the ibs, skip, and count options to grab the appropriate area.  Unfortunately, I'm not sure how to calculate the right values for these parameters.  Perhaps someone else can help you with that--you might want to see if someone on IRC can, for example.

---

### Post by burk on 2006-09-07
I asked in the gparted-forum, and they said I wouldn't be able to save my partition with gparted, and told me to use fdisk instead. I fount a tutorial on how to do it with fdisk, and tried to follow it. Somehow it went wrong, and I got "bad superblock" errors when trying to access the partition. So I tried to fix that problem too by following a tutorial, but it didn't work out. Then there was no other solution than reinstalling ubuntu, but since I was smart enough to put my /home on a separate partition all my data was ok...

But thanks anyways..

---

