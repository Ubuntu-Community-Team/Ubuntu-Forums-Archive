---
title: "Linux on Raid 0 ever?"
date: 2010-07-26
forum: Hardware
---

### Post by brooklynzoo81 on 2010-07-26
Hello all.  I have a AMD64X2 4200 A8N32-SLI Deluxe nforce4 SLI X16 with the Silicon Image 3132 Raid controller.  I have two 250Gb HD setup in raid 0.  I tired using the alternate cd but have no idea on how to properly setup raid with Ubuntu.  The CD picks up my raid as one whole 500GB disk but i am not sure how to proceed with partitioning.  I tired to let the cd do it automatically but it fails when it's about to write changes to the HD.

---

### Post by paulisdead on 2010-07-26
Are you dual booting this machine with Windows?  If not, then there's no reason to use the silicon image or motherboard RAID, since those are still really software RAID implementations.  Dmraid, which is the linux package that can deal with those "RAID" controllers, is pretty hit and miss, and the reliability is suspect.

If you're not dual booting, just use Linux software RAID.  You will need the alternate install CD to create and install onto a software RAID array.  The regular livecd does not include the option.

---

### Post by brooklynzoo81 on 2010-07-26
Thanks for the reply.  I am using the whole drive for Ubuntu.  I am getting stuck as to how to setup the Linux software raid. And how to go about partitioning all of this. I already have the Alternate CD ready to roll.

---

### Post by paulisdead on 2010-07-26
First make sure Linux is seeing them as 2 separate drives, and it's not seeing them as the RAIDed volume you made on Silicon Image controller.  If it is seeing at as one volume, go into the controller's BIOS and make sure to break the volume and reconfigure them for single drive mode.

When you go to create the software RAID, keep in mind you're not so much RAIDing drives, you're RAIDing partitions.  You need to make /boot it's own partition, give it probably 500MBs or more if you're not going to clean up old kernels regularly.  The /boot partition MUST BE RAID1 and not 0, or you will not be able to boot from it.

I'm going by memory of the Debian installer here, so this might be a bit off.  As an example create a 500MB partition on both drives with Linux Software RAID as the type, then select the option to create a Linux software RAID, and choose those 2 partitions to be apart of it, and select RAID1.  Then you should see a software RAID device called something like /dev/md0, you can now select this, pick what file system you want on it, and give it the mount point /boot.  Then make another pair of partitions, like for / (root), swap or /home, create another software RAID with the right 2 partitions, this time selecting RAID0 for them, and then find the correct device and select the filesystem and mount point for them.  Repeat the process for however many partitions you're making.

I know it seems a tad confusing, especially since you RAID the partitions together and not the whole drives, but I've found Linux software RAID to be really reliable.  Plus if the motherboard or controller dies, you can always bring the array up on another computer, since the metadata gets stored on the drives themselves.

---

### Post by brooklynzoo81 on 2010-07-26
Thanks a lot for the good information. I will give a shot and let you know how it all turns out.  Hopefully i can have a full linux box on raid.

---

### Post by brooklynzoo81 on 2010-07-27
Thanks again for the info you posted.  I followed it and this video [http://www.youtube.com/watch?v=-x2rZe2Z9as](http://www.youtube.com/watch?v=-x2rZe2Z9as)  both came in very handy and i have finally setup my first Linux raid 0.  Not sure if i partitioned it right on my end.  I gave swap 12GB, root 160GB, 320GB to home, and 2.1GB to boot lol.  But with 500GB to play with i guess i just got sloppy.  It appears to boot up fine but i did notice that after the BIOS screen i see a very quick error of some sort and the floppy drive lights up.  Before this the cursor would blink very fast for about 20 seconds and then it goes into the OS.  


What if i wanted to get brave and setup and machine that has windows already on a raid 0 setup?  Would i be able to resize the setup?

---

