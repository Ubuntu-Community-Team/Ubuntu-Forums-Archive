---
title: "Using 6.06 LTS Live CD to clone NTFS drive?"
date: 2009-04-08
forum: Installation &amp; Upgrades
---

### Post by CoriolisSTORM on 2009-04-08
Got a question for all you good people. I bought another drive for my old HP Pavilion A320N desktop. HP said I had a free drive bay but I do not. So, I am trying to use 6.06 to clone my old drive to my new one. The old one is a 120 GB 5400 RPM Samsung. The new is a 500 GB WD 7200 RPM Blue Caviar. I plan on cloning the 120 and moving the image to the 500 drive. Then, taking out the 120 and replacing it with the 500. Then I want to take the 120, throw it in an enclosure and trying to use it to boot Linux from. Can this be done? Right now I'm most interested in getting the data from the 120 to the 500. Can I use the LiveCD to do this? Got a step by step? I'm terrible with the command line. These are EIDE drives.

---

### Post by mazato on 2009-04-08
What you want to use is is alive Knoppiz for this. For me is better at fixing things, but I guess you cand do it in Ubuntu too!

If you have one partition only in your old drive then:
sudo dd if=/dev/hda1 of=/dev/hdb1
In this case you have to make sure that the partition you are copying to is the same or bigger size than the source.

Yu can do many things with dd, you can save also save the disk image to a file, save the image over a network through SSH.You can mount an image file using the loopback ption.
etc
etc
let us know how it worked!

---

### Post by matrixblue on 2009-04-08
I would use a clonezilla live CD to do the clone then use a Hardy or Intrepid Live CD (better NTFS support) to resize the partition.

---

### Post by upchucky on 2009-04-08
ntfsclone makes images of ntfs drives and partitions

you can download it and create a bootable cd then boot from the cd to make the image of the unmounted partition.

---

### Post by CoriolisSTORM on 2009-04-08
The drive isn't mounted on my LiveCD boot. The LiveCD includes NTFSProgs which includes NTFSClone, I just can't figure out how to get it to work and haven't mounted the new drive yet either. How do I mount them? One isn't even formatted yet. The reason I'm trying to do it with an Ubuntu live CD is I'm on dial up and had the disc lying about. It's so hard to download anything here...

---

### Post by upchucky on 2009-04-08
great, you cant image a mounted drive partition it has to be unmounted, you are half way there.

ntfsclone has to be burned to a cd then you boot the pc with that cd, it is pretty much almost automatic from there, couple of questions, clicks and wait for it to complete.

google for ntfsclone instructions if they were not included with the disk you do have.

---

