---
title: "Creating Partitions to Recover Data?"
date: 2008-09-03
forum: General Help
---

### Post by Crazy4Coffee on 2008-09-03
Hello all,
I have been trying to solve this for a couple of days, after the initial shock wore off, of course. I have done a lot of research and tried several different tools, but I could not find the answer to this particular question.

Ok, so I had a nice dual boot system with Windows XP and Xubuntu, but my twitchy little fingers had to mess with it and "clean up" the partition table. Stupid. Stupid. Stupid. I hang my head in shame.

Anyway, I had previously moved all my 25+ gigs of music to a shared partition formatted as FAT32. I was using a live cd and gparted to change the partitions. I have never had any trouble with it before. But this time it started spitting out all kinds of errors, but in the end looked like it had worked well enough anyway. To make a long story short(ish), I booted up Windows to sync my iphone and breathed a sigh of relief. However, when I went to boot up Xubuntu, it didn't work. 

I booted up in a live cd and gparted would not recognize any partitions at all. I used testdisk to try to restore the partition table, which I think made the situation worse because now it recognizes the ext2 and ext3 partitions, but not the windows ones, which coincidentally hold all my data that I need. Don't worry, I have scolded myself severely for not backing up all of it.

So the question is this. How can I recover the data from the windows partitions? I can't mount them because what used to be /dev/sda5 is now blank. /dev/sda5 is assigned to a Xubuntu partition now.  If I create a partition in the space where my data is, will it automatically erase the data, or will it just provide a partition number for me to work with?  
Or if you have a solution that involves recovering and transferring data to another computer, I do have a double-ended usb cord and a crossover cable.
I really appreciate the help of all you experts trolling the forums helping sad people like me.

Edit: This is a laptop, so I can't take the disk out and put it in my desktop. :(

---

### Post by oilchangeguy on 2008-09-03
any computer shop should have an adapter to allow them to run a laptop hard drive in a desktop. i got one from ebay. for under 5.00.

---

