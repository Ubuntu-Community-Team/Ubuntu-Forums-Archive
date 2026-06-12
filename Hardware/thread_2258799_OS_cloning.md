---
title: "OS cloning"
date: 2014-12-30
forum: Hardware
---

### Post by user987 on 2014-12-30
I sucessfully cloned my Zorin OS on to a flash drive via dd.

The problem is that my HD was 8g and the flash drive is 16g, the flash drive shows 6.6g just like the HD.

I used Gpart and cannot expand the flash drive to get the extra free memory.

Is there another free program i can use to make the OS on the flash drive larger on my flash drive?

---

### Post by overdrank on 2014-12-30
Hi and did you unmount the the drive before you used Gpart?

---

### Post by user987 on 2014-12-31
D'ont remember if i did or not, but i did use the flash drive to boot up another computer and use gpart to expand the flash drive memory and it did not work.

I will boot up my original computer and then plug (mount) the flsh drive and see if gpart will let me expanded the memory and get back to you on the result.

---

### Post by overdrank on 2014-12-31
Ok the drive has to be unmounted before gpart can be used :)

---

### Post by user987 on 2015-01-02
Hi,
      i finally unmount and did get it to work, but all it did was let me move befofe or after space of the 6.6 ext4 partition.
what i want to do is get the 6g of unallocated partition to the right of ext4 and swap into the ext4 .

i guess what i need to do is move that whole unallocated partition into the ext4 patition and then get like 12.6 in the ext4

How do i do that?

---

### Post by weatherman2 on 2015-01-02
Can you post the output of this command:

```
sudo parted -l
```

?  That will help us understand how the flash drive is currently partitioned.

---

### Post by user987 on 2015-01-02
thanks for the quick response, but i don't have the flash drive on me , will get back as soon as i get home to run your command on the flash drive and post the result.

---

### Post by sudodus on 2015-01-02
This link might help you

[http://phillw.net/isos/linux-tools/9w/GrowIt.pdf](http://phillw.net/isos/linux-tools/9w/GrowIt.pdf)

---

### Post by user987 on 2015-01-03
Hi,
       Thanks for the pdf will read it later.
I use the code mention earlier and here is the results:
Model:SanDisk Ultra Fit(Scsi)
Disk/dev/Sdb:15.6GB
Sector size(logical/physical);512B/512B
Partition Table:msdos

Numbers    Start         End         Size      Type        File System   Flags
1              3146kb    6615mb     6612mb  Primary    Ext4             Boot
2              6620mb   9422mb    2832mb    Extented
5              6620mb   8206mb    1586mb   logical      linux-swap(v1)

---

### Post by weatherman2 on 2015-01-03
I assume there is free space (shown in Gparted) at the end of the device?  That is, on the "right" on the bar?  If not, the instructions below will not work.

Anyway, the solution is this:  delete the swap partition, extend the primary OS partition, then create a new swap.  The trick is, you also have to delete the extended partition.  Ubuntu created that as a container to put the logical partition inside.  But in this case, it wasn't necessary because you have only two partitions.  In old msdos-style partitions, only four primary partitions are allowed.  To have more, you can have one "extended" partition, which is a container for many more partitions.  In some cases you need that extended partitions, and for whatever reason Ubuntu likes to create one by default.  But you don't need it if you will be sure will have a maximum of four partitions on your disk.

Here's what I'd do (using another boot disk, while this one you're trying to extend isn't booted), using Gparted:

- delete the swap partition and then the extended partition.
- create a new swap partition at the END of the drive - do this by typing "0" into the number for amount of free space after the partition
 (you could create it as 1.5GB again or 1500MiB, the size it is now, or whatever size you want, really).
- resize/grow the primary partition to use the rest of the unallocated space.
- we are not creating a new extended partition, assume you won't need it.

A final thing after you've finished resizing/recreating your partitions: you need to edit the fstab file of your USB drive to update the UUID for the swap partition, because you deleted the old one and the new swap partition has a new UUID.  UUID is like the "serial number" of each partition - a random number really, just a long number used for the OS to tell partitions apart. Use the blkid command to find out what the UUID numbers are:

```
sudo blkid
```

One of the entries should be your new swap partition, something like this:

/dev/sdb2: UUID="6f1371b8-103e-4549-9c2c-77adee26f3ae" TYPE="swap"

Now mount the / partition of your USB drive, then edit the fstab file with a text editor:

```
sudo gedit /media/ubuntu/bhahblahblah/etc/fstab
```

("blahblahblah" is the name of your USB's / partition, if you didn't give it a human-readable label)

And find the one line that mounts the swap partition.  It will look something like this:

```
UUID=f61371b8-103e-4549-9c2c-77adee26f3ea none            swap    sw              0       0
```

Replace the old UUID (in my case, "f61371b8-103e-4549-9c2c-77adee26f3ea", yours will be different, and replace it with the value you found using the blkid command.

Save the file, shut down, and reboot your USB drive - should be good.

---

### Post by user987 on 2015-01-03
Weatherman2,
                     thanks for the input will implement it and let you know.

---

### Post by user987 on 2015-01-05
Weatherman 2,

                        I rellocated the ext 4 to 14G but 1 had 1.3G unallocated to  right  of ext4 so i play around and got 1.3 to the left of ext4 now.

Anyway when i went to mount ext4 with right click mount is not hightlighted.

Can you me specific code to mount and create the swap part which i assume  is the unallocated 1.3G
Also i am confuse with the blahblah part is that the ext4?

Again a more detail example since i am a relative newbie in linux.

Thanks

---

### Post by weatherman2 on 2015-01-05
You don't want the unallocated space to the left in Gparted.   Otherwise, you're going to spend a lot of time (hours?) moving the ext4 partition to move it.  Resizing a partition is easy when adding space to the end (the right) of a partition but not to the beginning (the left of in Gparted).

You can mount your ext4 partition directly to the /mnt directory during a live Ubuntu session instead of using the /media directory.  Here's a line to do that:

```
sudo mount /dev/sdb2 /mnt
```

Then you would edit the fstab file this way:

```
sudo gedit /mnt/etc/fstab
```

If you mount the partition with Nautilus (with the menu and the mouse) instead of using the mount command above, it will get mounted in the /media/ubuntu directory under some "blahblahblah" name that is the UUID of the partition. But it's usually the only partition shown there if you do "ls /media/ubuntu" .

---

### Post by user987 on 2015-01-06
Hi Weathertman2,

                            Got  the flash drive now with partition 1 as the ext4, 14G and Partition 2 extended 1G and 1G free space.
I then did sudo blkid to see what my old uuid for swap was but nothing show up

did a fdisk-l to see the names of disk and didnot see swap only ext4 and extened.

I guess i need a little more detail example on how to get the swap part.

I am getting closer but no cigar yet.

One thing though when i boot up with the flash drive on another computer it does work and shows it as a 14G drive rather then 6.6G drive like before, 
only thing missing is that swap portion.

---

### Post by weatherman2 on 2015-01-06
How did you get to this point?  Did you use the Gparted tool?

Did you delete the extended partition?  As I said, you don't need it.  You need only two partitions: the big ext4 partition for / and a swap partition.  But from your previous output, I don't know how you were able to grow the ext4 partition without deleting the extended partition.   The extended partition is only a "container" partition for other partitions - needed only when you want more than four partitions on a disk.  You will have only two so you don't need an extended partition.

You can create a swap partition with Gparted, in the allocated space you have left.  Gparted is a Gui-based tool.  It's easy to click on unallocated space, right-click and say "Create partition" and choose swap as the type.  Can you not get to that point?

---

### Post by user987 on 2015-01-07
Hi Weatherman2,

                           I was playing with the tabs on the top of gparted but once you told me to right click on the unallocated space i did get to that ponit to create the linux-swap whcih is sdb2.

I then did the sudo blkid to find the uuid, then use yourt mount command to enable ext4 all in the terminal.

  I then  went into disk utlity to check to make sure that ext4 was mounted.

After that i went in terminal to type your gedit commands to replace the uuid.

Nothing happen so i went into text editor type the commands and hit  enter and again nothing.

So any idea what happen here?

---

### Post by weatherman2 on 2015-01-07
Let's back up a little.  The file /etc/fstab in Linux is the file that is used by the operating system to mount partitions.

If you boot a live Linux, it also has its own /etc/fstab file, but you need to edit the one on your USB Linux installation.  So I suggested you mount the main ext4 partition (normally your /  or root filesystem when you have booted Linux from that USB) in some other directory.  You must first mount that partition before you can access the fstab file to edit it with a text editor.

I suggested you mount it to the /mnt directory (a standard "place holder" directory in Linux where you can mount partitions, but don't have to).  You can mount the partition anywhere, as long as you then know where to find the /etc directory (and then edit the  fstab file that lives in that directory).

If you mount it to /mnt then you'd find the file under /mnt/etc/fstab .  If you mount it somewhere else - say /media/ubuntu/1234 or whatever directory you dream up - then you'd edit it as /media/ubuntu/1234/etc/fstab .

Before you try to edit the file, make sure you have mounted the partition first.  For example, if you have mounted it to /mnt, then do this in terminal:

```
ls /mnt
```

Are there some files/directories there?  If not, then you have not correctly mounted the partition there.  Make that work first.  Once you do, try this:

```
more /mnt/etc/fstab
```

That shows what the file looks like before you edit it.  There will be a file there before you start - you just have to modify it, modify that one line.

You can use any text editor you wish (but I wouldn't use LibreOffice because it may try to add "smart formatting" to a plain text file.).  But you will need to edit it with elevated privileges with the "sudo" command.  I suggested gedit, but if you don't have that text editor, use something else.

---

### Post by user987 on 2015-01-10
Hi Weatherman2
                          Finally got everything working.
Thank you for your patiance, really appreciate all your help.

---

### Post by weatherman2 on 2015-01-10
Great - glad you figured it out!  You may want to mark this thread as "solved."

---

