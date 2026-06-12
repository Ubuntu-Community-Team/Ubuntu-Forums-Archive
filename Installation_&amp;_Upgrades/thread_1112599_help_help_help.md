---
title: "help help help"
date: 2009-03-31
forum: Installation &amp; Upgrades
---

### Post by mattj7 on 2009-03-31
okay, I installed ubuntu "inside windows" from a boot cd i made.  I loved it, it was great, then when I was messing around with compiz, I broke it, and uninstalled it.  I re-installed it, and then i broke it again, im not even sure how.  So this time I decided to install it the real way from a live usb drive.  I was in the installation when i ran into problems.  I accidentally clicked on the dvorak keyboard.  I didn't realize this until i had already made the partion for ubuntu.  I then clicked back to attempt to correct the problem, it showed me that I only had a couple gigabytes left, and it showed the previous ten gigabyte partition as "free space" I clicked cancel, as I did not want to install it on yet another, 2gb partition.  now I'm in windows with almost no free space, and my hard drive is smaller because of the partition. I have a found.000 folder that seems to make up the partition, can i delete this to fix the problem? HOW DO I FIX THIS!?!??!?!?!!? HEEELLLLLPPPPP

P.S.  I have a 80gb hard drive, with 7gb on a seperate drive for vista backup (it works, and has saved me a few times) so that leaves me with 67 gb  on the c drive.  It is almost full and i have (had) about 13 gb free.  I want to have around 10-6gb for my linux partition. PLEASE HELP ME I'LL LOVE YOU FOREVER

Update: I deleted the found.000 and now I'm rebooting Please someone help, i thought i'd actually get help by posting in these forums...
Update: Restarted, and now I have alot more free space, but my hard drive is still 58.3 instead of 67, meaning that the 8.7gb partition is still there, how do i get it to go back on my C: drive, or can i install linux on that partition... still no help on these forums, c'mon guys im begging you

---

### Post by Partyboi2 on 2009-03-31
You can boot the ubuntu live cd and use gparted (System>Admin>Partition Editor) to either delete the partition you created by mistake and return the unallocated space to windows or you can use gparted to create the partitions for ubuntu. You will need one swap (about x2 of onboard ram) and a ext3 partition for the system files and data. Then when you install ubuntu choose the manual option and set the mount point for the ext3 partition to /

---

### Post by mattj7 on 2009-03-31
thank you thank you thank you, idk what you just said, you lost me after partition editor.  Thats exactly what I'm going to do. I'm going to delete the partition, and then restart and install it again without messing up.  If what you said was important, and this will not work, then let me know.  I'm off to reboot!

---

### Post by Mark Phelps on 2009-03-31
Post deleted.  You already have an answer.

---

### Post by mattj7 on 2009-03-31
actually, im just returning from the wonderful land of rebooting and running ubuntu on a live disk. turns out, i can't delete the partition with gparted.  I have no idea why, i can delete the windows partition, but this one shows up as "unallocated" and i can't do anything accept view information about it, which tells me nothing.  How do i delete this cancer off of my hard drive.  Is there anyway, please don't delete the thread just yet, i dont have an answer yet

---

### Post by Partyboi2 on 2009-04-01
Unallocated space is empty space, you cannot delete empty space,  use gparted to resize and increase your windows partition to take up all the unallocated space.
When you have booted the ubuntu live cd and opened gparted, highlight your windows partition and right click and select 'resize/move' and increase the size to use all the unallocated space.

---

### Post by SubNetMask on 2009-04-01
> **mattj7 said:**
> actually, im just returning from the wonderful land of rebooting and running ubuntu on a live disk. turns out, i can't delete the partition with gparted.  I have no idea why, i can delete the windows partition, but this one shows up as "unallocated" and i can't do anything accept view information about it, which tells me nothing.  How do i delete this cancer off of my hard drive.  Is there anyway, please don't delete the thread just yet, i dont have an answer yet

Dude wow...
There's like 100 free software things online that can format HDs,Get hiren's Boot CD, and delete every partition you can, than format the unallocated space, then do a clean install of ubuntu.

---

### Post by Mark Phelps on 2009-04-01
Hey -- chill out!! You really need to take a breath and calm down.  There's no "cancer" on your drive, just a bunch of extra partitions.

You can't delete partitions that are mounted, so in the Partition Editor, once you select a partition, click the Partition menu item, then select Information.  Under Status, it should say Not Mounted.  If it says something else, go back to the Partition menu and select Unmount. Also, every operation in the Partition Editor requires two steps: selecting the operation, clicking the Apply arrow.  Make sure you do both.

Also, if you want to expand your Windows OS partitin and you're running Vista, do NOT use the Ubuntu installer or GParted to resize your Vista OS partition; boot into Vista and use the Disk Management tool to do that.  Using the Ubuntu installer or GParted to resize the Vista OS runs the risk of corrupting the OS partition, which will require some work (including a Vista DVD) to get it working again.

If you're running XP, though, you should be OK though.

---

