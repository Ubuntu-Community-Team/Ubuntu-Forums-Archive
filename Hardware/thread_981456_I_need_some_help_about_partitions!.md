---
title: "I need some help about partitions!"
date: 2008-11-13
forum: Hardware
---

### Post by mvmacd on 2008-11-13
Hi, I installed Ubuntu, and now it is the only operating system, on my laptop. When I installed it, I think I didn't do the partition thing right, and now there are 16.53 GB of hd (out of the 37.2 GB of the whole hd), that I can't use. :confused:I installed Gparted, and tried to unmount the partition that I can't use, and it won't unmount  (look at the screen shot). Can anyone tell me how to get my hd back :cry::cry::confused::confused::confused:??? any help would be appreciated!


[IMG]http://img291.imageshack.us/img291/6876/22602334wa1.png[/IMG]

---

### Post by coolen on 2008-11-13
That 16.53 Gb partition is your root directory. With your setup, everything about Linux that's stored on your hard drive is stored there, so it can't be unmounted when Linux is running.

I'm assuming you selected the option to use the entire hard drive. For you, I'd recommend the following scheme:

1Gb linux-swap (this acts like extra memory for your computer when running Linux. I always put it at the beginning of the drive to minimise head movement, thus increasing read/write speed).
5Gb ext3 partition (mounted at /)
10Gb ext3 partition (mounted at /home). You can up this to 15Gb if you want, but remember, it's easier for Linux to access your Windows partition than the other way around.
The rest: NTFS partition (mounted at /media/win or anything else you want under the /media or /mnt directories).

To do this, you'll need to boot to the Live CD, open Partition Editor (System -> Administration, I think) wipe the drive (assuming there's nothing important on it now. If so, BACK IT UP!) and format it as above (don't worry about mount points).

Then, install Windows to the NTFS partition.

Pop the Live CD back in, and when you get to the partitioning stage, select manual. Edit each partition, giving them the mount points above. You'll need to format the first of the ext3 partitions (possibly the other one, too. The installer will complain if you do that wrong).

---

### Post by taurus on 2008-11-13
Not sure what you are trying to do here?  First off, you have one large swap partition there, /dev/sda1--20GB!  Then, you cannot unmount a partition that you are currently used, /dev/sda5.  That's why you see the error message when you try to unmount it.

What do you mean you cannot use 16.53GB of space on your harddrive?

---

### Post by Mardoct909 on 2008-11-13
If you haven't saved anything to it yet, I'd recommend reinstalling and letting Ubuntu do the partitioning for you. Your partitioning scheme is... illogical and rather wasteful. You DON'T need 20 GB of swap space.

---

### Post by mvmacd on 2008-11-13
> **coolen said:**
> That 16.53 Gb partition is your root directory. With your setup, everything about Linux that's stored on your hard drive is stored there, so it can't be unmounted when Linux is running.

I'm assuming you selected the option to use the entire hard drive. For you, I'd recommend the following scheme:

1Gb linux-swap (this acts like extra memory for your computer when running Linux. I always put it at the beginning of the drive to minimise head movement, thus increasing read/write speed).
5Gb ext3 partition (mounted at /)
10Gb ext3 partition (mounted at /home). You can up this to 15Gb if you want, but remember, it's easier for Linux to access your Windows partition than the other way around.
The rest: NTFS partition (mounted at /media/win or anything else you want under the /media or /mnt directories).

To do this, you'll need to boot to the Live CD, open Partition Editor (System -> Administration, I think) wipe the drive (assuming there's nothing important on it now. If so, BACK IT UP!) and format it as above (don't worry about mount points).

Then, install Windows to the NTFS partition.

Pop the Live CD back in, and when you get to the partitioning stage, select manual. Edit each partition, giving them the mount points above. You'll need to format the first of the ext3 partitions (possibly the other one, too. The installer will complain if you do that wrong).


"I'm assuming you selected the option to use the entire hard drive."

No, I didn't, but I've been thinking of reformatting, and start over,and select the option "use the entire hd." If I put windows on, then secected that option, would that wipe out windows (and reformat, like it did, when I installed Ubuntu)??? Because I really want to have both OS's on my laptop! Could you tell me how to do this :confused:??? thanks!

---

### Post by Mardoct909 on 2008-11-13
Install Windows, then put in the Ubuntu CD and go for the install. When it asks about partitioning, move the slider so Windows gets (half, or whatever) and Ubuntu gets the rest.

---

### Post by mvmacd on 2008-11-14
> **Mardoct909 said:**
> Install Windows, then put in the Ubuntu CD and go for the install. When it asks about partitioning, move the slider so Windows gets (half, or whatever) and Ubuntu gets the rest.


that is the whole reason I'm having this truoble! I tried that when installing Ubuntu, and it came up with some error message, and then the only options were to use the whole hd, or manual, which I did (I used manual).

---

### Post by Mardoct909 on 2008-11-14
Really? Because the auto partitioner should most certainly not have resulted in that partitioning scheme, which wouldn't work. Is the CD scratched? Try the "Check CD for defects" option when you boot it up. If it says it's clean, try what's below. Otherwise, get a new one and start again.

For one thing, the boot flag should be on the ext3 partition, not the 20 GB swap partition - which shouldn't exist anyways.

You could try doing it again manually. You need your windows partition at about 20 GB, a swap partition about 512 MB in size, and the rest for your ext3 file system.

When installing Windows, delete everything and make a partition for Windows that's only 20 GB or whatever you want for it. Do the whole installation and move on to the Ubuntu install. Make the swap partition first, about 512 MB should do, and them make an ext3 partition with the rest of the empty space on the hard drive. Its mount mount should be "/". (No quotes.)

---

### Post by mvmacd on 2008-11-14
> **Mardoct909 said:**
> Really? Because the auto partitioner should most certainly not have resulted in that partitioning scheme, which wouldn't work. Is the CD scratched? Try the "Check CD for defects" option when you boot it up. If it says it's clean, try what's below. Otherwise, get a new one and start again.

For one thing, the boot flag should be on the ext3 partition, not the 20 GB swap partition - which shouldn't exist anyways.

You could try doing it again manually. You need your windows partition at about 20 GB, a swap partition about 512 MB in size, and the rest for your ext3 file system.

When installing Windows, delete everything and make a partition for Windows that's only 20 GB or whatever you want for it. Do the whole installation and move on to the Ubuntu install. Make the swap partition first, about 512 MB should do, and them make an ext3 partition with the rest of the empty space on the hard drive. Its mount mount should be "/". (No quotes.)


Let me repeat myself. I didn't use auto partitioning, because I selected that option, and it gave me an error message, then that option dissapeared. So I did manual, and didn't do it right, so it was messed up. so anyway, I installed windows on the partition that that was like 20 GB (not the root partition, at least I don't think I did), and now it got rid of Linux. so I'll see if I can get the whole thing straighten out, by reinstalling Linux, and see if the auto partition thing will work.

Oh, and if I select use the whole hd, will it wipe out Windows?? because I want to be able to switch OSes, between Linux, and Windows.

---

### Post by psusi on 2008-11-14
Reinstall Windows, then Ubuntu.  While installing Windows, just have it create a partition that DOESN'T use up the whole drive, then tell Ubuntu to install to the remaining free space.

---

### Post by shadow1983 on 2008-11-14
If your willing to reinstall both again, then you could try booting up your windows xp disc, when it asks you what partition to use, delete them all so your whole HDD says unformatted partition then tell it to create a new partition using your whole HDD. 
Then reinstall windows, once thats installed. Boot up your ubuntu disc and then use the auto partition program and pick the size you want. I had an error message come up once when using the auto partition program and i found doing this sorted it out.

---

### Post by theozzlives on 2008-11-14
> **mvmacd said:**
> that is the whole reason I'm having this truoble! I tried that when installing Ubuntu, and it came up with some error message, and then the only options were to use the whole hd, or manual, which I did (I used manual).

Install Windows first, in the Windows setup partition half the drive. Then run the Ubuntu install and say "use free space". Or you can run Windows in a VirtualBox like I do.

---

