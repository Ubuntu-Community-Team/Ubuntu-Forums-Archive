---
title: "Creating .iso from block device &amp; restoring to disk"
date: 2010-11-12
forum: Hardware
---

### Post by RyanRahl on 2010-11-12
Hi, I have some print controllers that I want to be able to restore easily and one way to do it is to use a disk image. Basically I have a 20GB laptop IDE drive with 3 separate FAT16 partitions and I want to make an image of the entire disk with the 3 file systems contained in one iso. Then I want to be able to use that image to make duplicates of the original disk. The boot record and everything needs to be copied exactly, I have used partimage before and it doesn't do exactly as I need because it will only allow me to do one partition at a time. I have the drive connected to a USB adapter and it shows as 'sda' for the device with 'sda1' 'sda2' and 'sda3' as the partitions. I'm guessing I can create an iso with mkfs or rsync or something but I'm not sure how. Also I am not sure how to put the image on a disk properly once I have acquired the image. What is the best way to accomplish this task? Thanks. =)

---

### Post by Fafler on 2010-11-12
dd if=/dev/sda of=somefilename.img

To duplicate:

dd if=somefilename.img of=/dev/sda

---

### Post by RyanRahl on 2010-11-12
That worked perfectly, thank you. Is there a way to compress this data or ignore blank spaces while it is being written? The disk across all three partitions only contains about 250MB of data with a bunch of extra space for the end user to store scan jobs and reprint data on. It has 2 1GB partitions as 'IP-511' and 'BACKUP' for OS and recovery and a 16GB partion 'DATA' for the user. When I make the image it comes out as a ~20GB file when there is really only 250MB of data. 

I checked out the man page for the dd command, thanks again for pointing out such a useful tool.

---

### Post by Fafler on 2010-11-12
First, mount each partition and do a

dd if=/dev/zero of=/path/to/filesystem/alotofzeroes

Let it run until it stops after complaining the filesystem is full. Delete the file afterwards. Now, all the free space is made up of easily compressable zeroes, instead of old, abandoned data. FAT has a file size limit, i think it's 2 gb, so for the 16 gb partition, you need to repeat without deleting the files undtil the filesystem is completely full. Now make a new image and compress it with

bzip2 --best somefilename.img

The outputfile will be somefilename.img.bz2 and it will be a lot smaller than the original.

---

### Post by RyanRahl on 2010-11-15
> **Fafler said:**
> First, mount each partition and do a

dd if=/dev/zero of=/path/to/filesystem/alotofzeroes

Let it run until it stops after complaining the filesystem is full. Delete the file afterwards. Now, all the free space is made up of easily compressable zeroes, instead of old, abandoned data. FAT has a file size limit, i think it's 2 gb, so for the 16 gb partition, you need to repeat without deleting the files undtil the filesystem is completely full. 

I did this and now it is telling me all the partitions are of an unrecognized type and I cannot mount any of them. It seemed to do exactly as you said but I could not find the output file. I'm trying to figure out what I did wrong and possibly repair these partitions.

---

### Post by Fafler on 2010-11-17
Exactly what did you write?

---

### Post by Fafler on 2010-11-17
If you do still have the first image you created, don't delete it or mess around with it. We might really need it to get your data back.

---

### Post by RyanRahl on 2010-11-23
Yeah I still have it, sorry it took so long to get back. It's been a bit crazy. I think I may have overwritten the partition itself instead of filling the blank space with zeros. I forgot exactly what I did so I'm going to try this again since I still have the original. When you said 

"First, mount each partition and do a

dd if=/dev/zero of=/path/to/filesystem/alotofzeroes"

I think I may have written to the block device instead of the mounted file system. Just to be clear, I want to mount the file systems and write zeros as a file on the partitions and then delete the zero file. At that point I create the image and it should only be the size of the data that's on it or does that come when I use the bzip? Thanks again for your help.

---

### Post by Fafler on 2010-11-24
That is exactly what you should do. First copy the data back. And keep the image file until you are sure everything is alrigt. The partition image will take up as much space as the the partition until you compress it. After compression it should take up less space than the actual data on the partition.

Also, as you might have learned now, tools like dd are really powerful and quite dangerous. They do what you ask without question, so you should always double check everything.

---

### Post by RyanRahl on 2010-11-26
Ok, so it all worked out with the following steps:

mkdir /media/part1
mkdir /media/part2
mkdir /media/part3
mount /dev/sda1 /media/part1
mount /dev/sda2 /media/part2
mount /dev/sda3 /media/part3
dd if=/dev/zero of=/media/part1/zerofile
dd if=/dev/zero of=/media/part2/zerofile
dd if=/dev/zero of=/media/part3/zerofile
dd if=/dev/zero of=/media/part3/zerofile1
dd if=/dev/zero of=/media/part3/zerofile2
dd if=/dev/zero of=/media/part3/zerofile3
dd if=/dev/zero of=/media/part3/zerofile4
rm /media/part1/zerofile
rm /media/part2/zerofile
rm /media/part3/zerofile
rm /media/part3/zerofile1
rm /media/part3/zerofile2
rm /media/part3/zerofile3
rm /media/part3/zerofile4
dd if=/dev/sda of=/home/user/Desktop/ip-511a.img
bzip --best /home/user/Desktop/ip511a.img

So there were five zero files on the 18 GB partition because the filesize limit it 4GB and it took 5 to fill the disk. The image was roughly 20GB and it compressed down to 57MB so that was an awesome improvement and it is now very compact. So I guess the only question I have left is: Can I write the image to the device without having to decompress it to a 20GB file first? That way I won't have to make sure to have 20GB of free space every time I need the image.

Just as a note this is for use on a Koncia print controller model IP-511a running VxWorks.

---

### Post by Fafler on 2010-11-27
That was exactly what i wanted you to do. Glad you didn't lose your data.

You can do the decompression and writing in one step:

```
bunzip2  /home/user/Desktop/ip511a.img | dd of=/dev/sda
```

---

### Post by RyanRahl on 2010-11-27
Perfect, this will save me a lot of headache in the future. Thank you for your help. I'm imagining an almost unlimited amount of uses for this information.

---

