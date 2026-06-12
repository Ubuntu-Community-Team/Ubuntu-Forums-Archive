---
title: "resize partitiions w/gparted"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by jwazzz on 2007-02-18
I set up a dual boot with xp and Edgy. Im really starting to like edgy. I partitioned my hd like this:
hda1  - xp
hda2 - swap
hda3 - /
hda4 - home

Now I see that I allocated too much space for hda3 and not enough for hda4.
I would like to resize the partitions by reducing hda3 and putting freed space into hda4.

When I tried it I got an error. I think I can only have 4 partitions. 
Is there a way to do this without messing up my hd?
Also when I open naultilus, I can see hda1, but not hda3 or 4. Is there a way to see hda3 and 4 in naultilus?

---

### Post by the ev on 2007-02-18
I think that Naultilus will show your root partition, hda3, as "File System", so it won't have the hda3 label attached to it.  By the same logic, your home directory, /home/user, is hda4.  Ubuntu integrates those drives in seemlessly within the file browser.  

As for the partitioning problems (and again, I'm no expert), I shouldn't think there should be a limit on the number of partitions you can have - well, in so much as you have space for *n* partitions.  I had some errors using GParted when paritioning my other system (I was triple-booting Ubuntu, Vista, OSX86, and I had a fourth parition available for testing other distros), and I found that if I just did one step at a time, it seemed to work fine.  So if you had told Gparted to (1) resize a partition (2) create a new partition, just tell it to do (1) then click apply, then go back and tell it to do (2) and click apply.  Seemed to work for me.  I don't know if its a problem with GParted or what, but sometimes I've found it doesn't like queuing commands.  I couldn't tell you why, though.

And yeah - Edgy's great.  I'm loving in on my tablet; so much faster than XP Tablet Edition.

---

### Post by lichmeister on 2007-02-18
> **jwazzz said:**
> I set up a dual boot with xp and Edgy. Im really starting to like edgy. I partitioned my hd like this:
hda1  - xp
hda2 - swap
hda3 - /
hda4 - home

Now I see that I allocated too much space for hda3 and not enough for hda4.
I would like to resize the partitions by reducing hda3 and putting freed space into hda4.

When I tried it I got an error. I think I can only have 4 partitions. 
Is there a way to do this without messing up my hd?
Also when I open naultilus, I can see hda1, but not hda3 or 4. Is there a way to see hda3 and 4 in naultilus?

if i understand your situation correctly [and im no expert either :)] you are trying to edit an active, mounted partition? if either hda3 or 4 is mounted,, you will be prevented from making any changes and im assuming you are logged into ubuntu [on hda3] while doing this so unmounting hda3 is out of the question... soooo...

1: back up anything on either partition that that you would be sad to lose IMPORTANT! ive never lost data to a partition resize but it does happen, apparently, so if you are in doubt BACK IT UP!
2: load your ubuntu live cd and reboot your computer
3: resize your partitions with gnome partition editor [System>Administration, idb] and reboot
4: keep your fingers crossed that nothing was corrupted during the resize

just a note on / size... imo you should leave at least enough room on  / for a dvd image... i made the mistake of shrinking my / partition to 4 GB and discovered later that many of my installed programs made prodigious use of the /tmp directory... nautilus cd burner for example puts the disc image in /tmp and i have no idea how to tell it to place the temp iso elsewhere... i guess thats probably why some people recommend a seperate partition for /tmp :?

peace 

the lichmeister

---

