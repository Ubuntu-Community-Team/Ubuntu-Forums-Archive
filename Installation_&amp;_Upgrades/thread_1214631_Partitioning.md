---
title: "Partitioning"
date: 2009-07-16
forum: Installation &amp; Upgrades
---

### Post by BobJam on 2009-07-16
I installed Ubuntu, and now I have a dual boot machine (Grub).  That part's fine.

But, I think I screwed up.

The Ubuntu Update Manager came up, and showed some updates to download.  So I clicked on "Install", and then it said I didn't have enough disk space for the measly 300 some MB's of the updates.

So I bounced back to Windows and took a look at what the partitions were, and here's what I saw:

[IMG]http://i510.photobucket.com/albums/s346/rbjamie/Ubuntu/Partitioning/1Partitions-2.gif[/IMG]

It looks like Ubuntu just took the bare bones of what it needed (only 2.33GB for the OS and 173MB for the swap) and there was only about 120 some MB free on the Ubuntu OS partition.

I probably should have chosen the "manual" option when it displayed that installation page about partitioning, and sized the thing myself (my Windows partition is some 77 GB's, but only 20 some are used, and there is about 55 or so free).  On the installation page about partitioning, I chose the option to have it install itself "beside the Windows partition".  I saw a brief message about my selection being irreversible (and usually when I see something like that, I press "Cancel" until I can look into it . . . but this time I pressed "forward" . . . the Ubuntu version of "next" I guess).  I think this is where I really screwed up.

So I tried Ubuntu's "gparted", but the "resize" option was grayed out.  I wanted to see if I could resize the partition with Ubuntu, but I couldn't figure out how to do it (actually, I'm not real sure it can BE done).

I have plenty of free space, and I had planned to reallocate about 20GB for Ubuntu.  Had I chosen that "manual" option, I probably could have done that.  Why I didn't choose "manual" is beyond me.  That was a real stupid move.

I have PartitionMagic and am tempted to try to resize with that, but I'm pretty snakebit now, and all I really want to do is wipe out the Ubuntu installation and start over from the CD I made from the ISO.  But I'm not sure how to do that either.

So, my most pressing questions are:[INDENT][FONT=Arial][COLOR=Blue][B][I]How do I wipe out all the Ubuntu stuff and start over?

If I wipe out the partitions, will that mean Ubuntu is completely gone?  (Which is exactly what I want).

Do I remove/delete the partitions through windows?  If so, exactly how do I do that?

Or do I remove/delete the partitions through the Ubuntu CD . . . and if so, how?

Or do I just do the install again, THIS TIME CHOOSING "MANUAL" sizing, and it will remove the first install?
[/I][/B][/COLOR][/FONT][/INDENT]TIA
****

---

### Post by Partyboi2 on 2009-07-16
You can boot a ubuntu live cd and use partition Editor (System>Admin>Partition Editor) and right click on the window ntfs and select 'unmount' then you should be able to resize it down, then use the resize option to increase the size of Ubuntu. Remember to backup your important stuff before working on partitions.

---

### Post by az on 2009-07-16
This is not that big of a problem.  The reason that the partition was greyed out in Gparted was because you were running your OS from that partition.  To safely resize a partition, you need to unmount the whole disk.  

As mentioned, running from the live cd should do the trick.  Just use the partition editor to shrink your windows partition further and resize your Ubuntu partitions.  You should be good to go.

The Package manager should be able to reinstall any packages that have not been properly installed.

---

### Post by Mark Phelps on 2009-07-17
Sorry to "break from the pack" here ... but ... strongly recommend that if your Windows OS is Vista, that you do NOT use GParted to shrink it to get more room for Ubuntu.

Recommend an alternative as follows:
1) Boot from Ubuntu LiveCD
2) Open the Partition Editor
3) Shrink the FAT 32 partition to make room
4) Check the properties of the Swap partition. Make sure Swap is turned off. Unmount the Swap partition (if not already unmounted)
5) Move the Swap partition to the right, up against the FAT 32 partition
6) Resize the Ubuntu partition to take up the free space
7) Reboot without the CD

You should now have a larger Ubuntu partition and not have space problems.

---

### Post by BobJam on 2009-07-18
@Mark Phelps,

Fortunately, my Wndows OS is NOT VISTA, it's XP HE SP3.

However, the repartitioning was not as straightforward as I had hoped.  Nevertheless, I did manage to do it (after several hours of puckering).  Am composing an account of that saga to post on these forums.

Is not just for purposes of idle chit-chat, but so that other noobs can benefit from my own twisted experience.

I have my dual boot of Windows and Ubuntu up and running now.  Stay tuned . . .

---

### Post by rcbinwi on 2009-08-03
I am a newbie.  I set up a dual boot system, too, and am having the running out of disk space problem.  It seems strange that one would have to set the partitions manually if one hopes for any upgrades in the future.  Or is there a way for the Ubuntu partitioner to automatically set space for "future growth" that I'm missing.

I guess I'll know for the future.  I'll try to do the recommendations put forth here, and I'll post any problems I have.

---

