---
title: "Cloning a harddrive with different partition sizes"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2009-01-02
I have a laptop with a 250GB drive that I currently triple-boot. I am running out of space and already purchased a 500GB drive.

However, I am not sure how to duplicate my old drive to the new one, since I will need to do more than just copy over the data.

Vista is my main OS, but I figured (correct me if I am wrong) that this would probably be easier to do in Ubuntu, I do have Acronis True Image 11 for Windows if that helps.

Although my laptop only has one SATA port, I have a USB SATA dock which I can use to copy the data.

I want to AVOID re-installing Windows or Ubuntu, I don't care about the data in the other partitions. It would be nice if I could just copy over my "STORAGE" partition as well, but if need be I can backup the data to an external drive then copy it back later.

My current partition setup is as follows I (Ignore the USB drive):

[http://i12.photobucket.com/albums/a207/Cyber_Akuma/Forum%20Hosted%20Junk/CyberAkuma-LaptopHarddrive.png](http://i12.photobucket.com/albums/a207/Cyber_Akuma/Forum%20Hosted%20Junk/CyberAkuma-LaptopHarddrive.png)

I have three primary partitions:

A 1.5gb NTFS system partition (came pre-installed with the system, laptop seems to fail to detect the harddrive without it, and id really rather not mess with it since its only 1.5gb)

A 142GB NTFS Vista partition

A 15GB HFS+ MacOS Partition

And for extended:

A 10GB exf3 Ubuntu 8.10 partition

A 60GB FAT32 Storage partition, meant to be a partition that all operating systems on the laptop can easily read/write to (hence why its FAT32).

A 1.5GB Swap Partition

Now, as I said, the problem with just copying these partitions over is that I want to resize most of them, as well as add one, its just a simple duplicate.

My current plans are to:

Increase the MACOS partition to 20GB

Increase the Ubuntu partition to 25GB

ADD another 25GB partition for Open-Suse(quad-boot, I want to try out both distros to see which one I like) between the Ubuntu and STORAGE partitions

Most likely keep the swap partition the same (laptop has 4GB of ram, not sure if I even need the current 1.5GB as it is but I added it just in case)

And then whatever space is left ill decide how big I want the Vista and Storage partitions to be. I primarly want to focus on the Vista partition since I use that far more than the others.

So then, what would you recommend I do? How can I go about doing this? Especially in a way that copies over all my MBR/boot information.

Preferably, if such a thing is possible, I think the easiest way would be if I can first copy over the 1.5GB system partition, then (preferably with a GUI) plan out how the rest of the harddrive should look after I am done adding/resizing all the partitions, then apply the partitioning and copy over the data, if its not possible to partition and copy in one step.

Kinda like how in Acronis I can muck around with all sorts of changes to my harddrive and see what it would look like before hitting Apply, but I want to do it all in one shot.

The biggest problem with this, is since I will be doing the Vista and STORAGE partitions last since I will decide how much space to give them AFTER I change all the other partitions, I can't just add each partition in one by one in order, I need to way to add the other partitions in first (at least in a preview mode before the actual partition data is written to the harddrive) THEN add in/resize the Vista and Storage partitions. It dosen't help that the Vista partition is near the beginning and STORAGE partition is in the middle...

Sorry if I made this post a little confusing, I will try to clarify any questions anyone has about this.

So.... how would you recommend I go about doing this?

---

### Post by Pumalite on 2009-01-02
The only thing to keep in mind here is that the image to be restore has to go into a partition equal to the one it had or bigger. Don't forget the 4 primaries per drive rule. If you are going to use a mix of IDE and SATA; keep this in mind:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Cyber Akuma on 2009-01-02
I can't just do an image restore because this is a drive with multiple partitions I am trying to clone, instead of a single partition, AND I need to resize the exsisting partitions on the new drive.

I know about the 4 primaries rule, this is why I currently have 3 primaries and an extended.

And no, this laptop only has a single SATA port.

---

### Post by my_key on 2009-01-02
I would do from a live cd with every filesystem on sda unmounted:
```

dd if=/dev/sda of=/dev/sdb
```

where sdb is the new drive.

If everything is cloned you resize the partitions.

---

### Post by Pumalite on 2009-01-02
Use Clonezilla. It can 'image' an entire drive.

---

### Post by Cyber Akuma on 2009-01-02
I want to avoid cloning THEN resizing the cloned partitions, because last time I tried that I ended up with corruption.

I want to create the partitions in the size I want then clone their contents, except the 1.5gb system partition, which I will just plain copy over.

---

### Post by my_key on 2009-01-02
Then you must do so. 

Create the partitions on the new drive. Copy all the files with something like rsync (with sudo, so you have all the files, but make sure to use the flags that preserve ownership and permissions. Otherwise all the files will be owned by root).

---

### Post by my_key on 2009-01-02
I just think of something. I 'm sure your OSes will boot fine after that, because rsync really is a magnificent tool, but you might need to reinstall grub to your MBR since that will not be copied. The ubuntu wiki has a great guide on that: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
The title suggests it's not applicable, but it basically deals with rewriting grub to the MBR, what most people need to do after they've installed windows, because windows writes it's own bootloader to the MBR.

---

