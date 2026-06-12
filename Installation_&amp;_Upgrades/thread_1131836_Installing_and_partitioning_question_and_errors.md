---
title: "Installing and partitioning question and errors"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by 2quick on 2009-04-21
Hello all!

I am trying to do a new install of Ubuntu 8.04LTS(from a CD) on a laptop with Vista already installed and running 64-bit version.  I have 4 G of Ram.  This is what I am thinking for partition size:

/-10G
swap-8G
/home-42G

When I click next to continue the install it gives me this error:

"Some of the partitions you created are too small.  Please make th following partitions at least this large (in bytes):

/home

If you do not go back to the partitioner and increase the size of these partitions, the installation may fail."

So it doe not specify how much larger it should be.  Also I was always under the impression that it really did not matter how large you /home partition was, that is just your personnel type files.  Thanks for the help!

---

### Post by ronparent on 2009-04-21
Something does not compute here (your conclusion also)??? The sizes in your post are appropriate. Are you sure you entered them in Gig.s?

---

### Post by 2quick on 2009-04-21
I am pretty sure I am looking right at the sizes, maybe a little sleepy eyed though:

ext3 / 9999 MB
swap   8030 MB
ext3 /home 42000 MB

---

### Post by ronparent on 2009-04-21
When you have selected the manual patition option on you first partition screen, I presume you find or have created sufficient unallocated space to create the new partiotions. If that is the case, prior to applying your partiotions would appear as such:

ext3  /  9.99GiB
swap     8.03GiB
ext3  /home 42.00 GiB

Again, provided you have sufficient unallocated disk space to create those partitions, the partitioning and installation should continue to a successful install! Are you leaving anything out?

---

### Post by 2quick on 2009-04-21
I believe that I have enough free space.  I re-sized the windows partition and that is where the free space came from.  I thought maybe that if I decreased the /home by one and 1mb and left 1 mb of free space maybe that would do it, but I received the same error message when clicking next.  This it what it currently looks like after setting the /home back to taking up the full free space.  This is a Windows Vista system with 1 additional partition acting as a storage drive:

Device           Type  Size   Used
/dev/mmcblk0
  /dev/mmcblk0p1 Fat16 1015MB 33MB
/dev/sda
 /dev/sda1       Fat32 11531MB 10800MB
 /dev/sda2       ntfs  100000MB 17300MB
 /dev/sda6       ext3/ 999MB   unknown
 /dev/sda7       swap  8030MB  unknown
 /dev/sda8       ext3/home 42000 unknown
 freespace             0MB
 /dev/sda5       ntsf  148509MB 81600MB

So the at the moment the only thing I am wondering is if it matters that I chose at the beginning for where to start.  Also does it matter that /sda5 is not in order? Also must any of the partition have to be primary?

Thanks for all the help and replies! :)

---

### Post by ronparent on 2009-04-21
I think I see the problem. Use gparted from the live cd to remove all the new partitions. Then create and extended partition for the entire now unallocated space. Now I believe you will be able to partition with no problem.

The numbers on the partitions are automatically assigned and are irrelevant to your problems. What is relevant however is that you cannot create more than 4 primary partitions (including the extended partition). Your complete ubuntu partitions, however many, will live nicely in the extended partition.

---

### Post by 2quick on 2009-04-21
> **ronparent said:**
> I think I see the problem. Use gparted from the live cd to remove all the new partitions. Then create and extended partition for the entire now unallocated space. Now I believe you will be able to partition with no problem.

The numbers on the partitions are automatically assigned and are irrelevant to your problems. What is relevant however is that you cannot create more than 4 primary partitions (including the extended partition). Your complete ubuntu partitions, however many, will live nicely in the extended partition.

Well I think that I finally got that done, but with some hurdles.  For some reason when in the liveCD it would initially not open up the konsole to start Gparted.  I would click on it and nothing would happen.  Then I would try to open something else and it would just hang there and basically freeze.  After three attempts I finally got Gparted running. I deleted everything it straightened it all out I believe.

So I restarted the computer and went to install mode and then when it tried to start the partitioning the cd stopped spinning and it froze up.  I did a md5sum on the image from my other computer and did a datacheck on the cd when I first placed it in the computer and everything is fine.  So I am downloading a new image to burn.  Would it make a difference if it was the 32bit vs. the 64bit?  I am trying to install the 64bit version.  It appears that it should work, the laptop runs 64bit Vista.

Thanks for the help as always! :)

---

### Post by ronparent on 2009-04-21
If you have a 64 bit cpu it should make no difference whether you install 32 or 64 bit version. I'm a bit confused though. From the live cd can't you simply open System > Administration > Partition Editor (gparted)???

---

### Post by 2quick on 2009-04-21
I was just trying to open it another way to see if it fixed the freezing problem.  I reburned the cd and Gparted opened fine throught the admin tab.  But when I went to shut it down there was an error that continuously scrolled on the screen, it was going to fast to read the numbers, but it said there was an error with the squashh.  Also when I have tried to go back in the liveCD it freezes up when trying to open applications.  Both on the 64 and 32 bit versions.  Have you heard of this before?

---

