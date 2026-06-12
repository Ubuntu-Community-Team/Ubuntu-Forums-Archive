---
title: "deleting contents of damaged SD-Card (for warranty replacement)"
date: 2015-04-20
forum: Hardware
---

### Post by kaefert66014235 on 2015-04-20
Hi there!

I have a 64GB SanDisk Ultra SD-Card that I think is damaged.
[http://geizhals.at/sandisk-ultra-sdxc-64gb-30mb-s-sdsdu-064g-u46-a754792.html](http://geizhals.at/sandisk-ultra-sdxc-64gb-30mb-s-sdsdu-064g-u46-a754792.html)
Sadly, it seems, there is nothing like SMART for those SD-Cards, but it surly behaves strange enough for me to assume it's damaged.

I can "delete" everything but one file (and the directory path to it) simply using rm in the terminal.
I use quotes, because if I delete everything but that one file, unmount the partion, and mount it again, everything is in its place again as it was before running the rm commands.

When I try to create a new partition table using gparted, it does not give any error, but strangely shows an "unknown" partition of the same size and at the same position afterwards where before was the exfat partition. This picture stays persistent when I close gparted and open it again, but when I remove the SD-Card from its reader and reinsert it my exfat partition along with all my content is back again. Deleting the partiton using gparted gives the same picture: no error, and afterwards an "unkown" partiton of same size and position as before.

When I try to delete the partition and create a new one in the same batch of operations, I get a message from libparted: "Can't have overlapping partitions."

I've tried shredding single files
```
shred -z -n 5 /media/kaefert/3131-3365/DCIM/596_0103/IMG_0115.JPG
```
and the device file as a whole
```
sudo shred -z -n 5 /dev/sdc
```

Both look like they work at first, but as soon as I unmount and remount the partition, all the content is there again.
Though with the device file on one shred run I got an IO-Error after a few hours, I did not yet let the device file shred command run till it finished, I'll probably try that one more time but I'm not really hopful.
> shred: /dev/sdc: fdatasync failed: Input/output error

I don't want to send an SD-Card with my private pictures to SanDisk, so if I can't solve this problem I'm more inclined to simply destroy the card physically and buy a new one instead of getting a warranty replacement..

Anybody got any ideas what else I could try, or maybe even an explanation for this strange behaviour?

---

### Post by kurt18947 on 2015-04-20
I'm not sure what distro you're using. If gparted were installed or available, I'd look at the SD card using that. Maybe delete and recreate the partition table. Or maybe try DBAN - I'm not sure if DBAN works on flash media but it's free to try. Just be VERY careful to select the right device. I'm pretty sure DBAN is unrecoverable, I don't know about Gparted operations . If neither of those work, I'd suspect the SD card is not writeable so you don't really have much choice except to destroy it. Just my take on it.

Another related thought I just had. I wonder what the formatting is on your card.  I think higher capacity (>32 GB.) devices may use exFAT. From Wikipedia:
[INDENT][B]
exFAT[/B] (Extended File Allocation Table) is a Microsoft file system optimized for flash drives. It is proprietary and patented. **exFAT**  can be used where the NTFS file system is not a feasible solution (due  to data structure overhead), or where the file size limit of the  standard FAT32 file system is unacceptable.
[/INDENT]

I've never had one of the exFAT formatted devices so don't know if they're partially readable under stock linux or not. There are packages in some repositories that enable reading and writing exFAT devices in linux. No idea about legality of their use.

---

### Post by kaefert66014235 on 2015-04-20
I do use Linux Mint 17.1 - which is a derivate of Ubuntu 14.04 LTS.
And if you had read my first post from beginning to end, you would have known that I tried gparted (both recreating partition table and deleting and creating a new partition) and it did not help..

---

### Post by kurt18947 on 2015-04-20
I didn't see your mention of Gparted.  Makes me think more about exFAT. I wonder if DBAN would work. Or using some utility from the O.S. (Windows?) that does recognize the device?

---

### Post by kaefert66014235 on 2015-04-20
hmm. well. but if the partition type "exFAT" would be at fault, then shredding the device file should work, which it doesn't..

---

### Post by kurt18947 on 2015-04-20
I'm not expert in this. I think shred works by overwriting a file with zeros or random bits. I'm speculating shred doesn't work because it would need to be able to write to the device. If the O.S. doesn't recognize the file format, how can it overwrite? I wonder about DBAN which I think runs independent of the installed O.S. It might be worthwhile to install the packages enabling read and write of exFAT devices. If you have Synaptic (my preference) or Software Center and search for 'exfat', you should find the required packages. There used to be a PPA required but I think the required packages are now in the Ubuntu repositories. From memory - it's been a while - the packages are exfat-utils (or exfat-utilities) and exfat-fuse.

---

### Post by kaefert66014235 on 2015-04-20
yes, your assessment of how shred works is consistent with my idea of it.

no, I don't agree that linux needs to know what format a file has, to be able to write to it (using shred) otherwise for example you wouldn't even be able to shred / delete an encrypted file when you don't know the encryption(key) - you can still read and write to such files, even though you might not be able to understand the content / know exactly what it is that you're overwriting or deleting.

The beauty in linux is that everything is a file, even devices and partitions, and you can backup and or destroy devices or files by using these "files" like /dev/sdc = device or /dev/sdc1 = partition. Even if your system doesn't know partition type, you can work with partiton files like those, and in a case your system can't read or doesn't know the format of the partition table, you can still operate on the device using the device file.

Of course, since I have been using exfat for a while now, because most modern cameras use this file system by now I have the necessary packages installed on most of my systems: "exfat-fuse" to be able to mount it in nemo (or nautilus in ubuntu's case) and "exfat-util" to be able to work with those partitions in gparted for example.

Still, I don't think that my problems are related to the partition type "exfat".

I did not know DBAN before you mentioned it here, it seems to be a very specific linux distro, for shredding every storage-device in a computer. that is definitely not what I want, and even though I have not found the exact list of tools it employs for the tasks, I doubt it has any magic weapon that I can not use in any other distro.

---

### Post by kurt18947 on 2015-04-20
If you already have the exFAT tools installed, I have no further thoughts. If you want to try DBAN, would it be feasible to disconnect any hard drives or other devices you don't want touched? I've never tried DBAN to wipe flash devices, just hard drives.

---

### Post by kaefert66014235 on 2015-04-20
well... I guess it would be doable, but it would be quite some work on my end, and I don't have any hopes that this would work better than anything I've tried yet. If you or somebody else could explain why you think it could help, I'd still be willing to try it.

Though I hope for someone to post other ideas ;)

---

### Post by ajgreeny on 2015-04-20
You could try one or other of these three commands in terminal, but be very careful to get the correct device; dd is also colloquially known as "**d**isk **d**estroyer" because if you get the wrong device you may wipe something other than the one you want.

I'm not sure but I think you may need to do this with sudo.
```
dd if=/dev/null of=/dev/sdx bs=512    #or:-
dd if=/dev/zero of=/dev/sdx bs=512    #or a bit faster:-
dd if=/dev/random of=/dev/sdx bs=1024
```

---

### Post by kaefert66014235 on 2015-04-20
/dev/random seems to only spit out data very infrequent at my system, I guess it's using user input like mouse movement.

I'm currently running this:
```
dd if=/dev/zero of=/dev/sdc bs=1024
```

and whats strange is, that it both reads and writes /dev/sdc (according to various monitoring tools) alternating.
`shred` does only write to it, without reading in between.

Okey, so it finished, but it doesn't change anything about the content that is shown, also after remounting..

> dd if=/dev/zero of=/dev/sdc bs=1024
dd: error writing &#8216;/dev/sdc&#8217;: No space left on device
62367745+0 records in
62367744+0 records out
63864569856 bytes (64 GB) copied, 8897,32 s, 7,2 MB/s

update, I've also tried this now:
> dd if=/dev/zero of=/dev/sdc1 bs=1024
dd: error writing &#8216;/dev/sdc1&#8217;: No space left on device
62351361+0 records in
62351360+0 records out
63847792640 bytes (64 GB) copied, 8889,69 s, 7,2 MB/s

but again, when I mount the partition again afterwards, everything is still there..

---

