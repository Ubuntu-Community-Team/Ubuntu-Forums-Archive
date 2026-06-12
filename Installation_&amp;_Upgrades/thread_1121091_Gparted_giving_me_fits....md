---
title: "Gparted giving me fits..."
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by xi_Slick_ix on 2009-04-09
So, for a quick background.  Trying to re-size an NTFS partition to make room for Ubuntu / Myth.  (so Yes it will dual-boot)

Athlon 3000
DFI LanParty UT nF3
2 gigs of ram
Nvidia 6600 256mb
Seagate 320GB SATA II HD (Running SATA I)
XP Media Center 2005

The HD in reality is around 298GB's and the capacity does properly show in Gparted.  Unfortunately, the entire drive is shown as unallocated space.

After searching through some other posts, I went ahead and took these screen shots...

[[IMG]http://i113.photobucket.com/albums/n225/halobravesfan06/Linux/th_gparted_unallocated.jpg[/IMG]](http://s113.photobucket.com/albums/n225/halobravesfan06/Linux/?action=view&current=gparted_unallocated.jpg)

[[IMG]http://i113.photobucket.com/albums/n225/halobravesfan06/Linux/th_Terminal.jpg[/IMG]](http://s113.photobucket.com/albums/n225/halobravesfan06/Linux/?action=view&current=Terminal.jpg)

My objective was to take the 100gb partition and move 80gb's of it into the 150gb partition, leaving the rest for the ubuntu install...

I can reformat the drive is push comes to shove.. I have all my data backed up, but if there are any suggestions to get around this 1st I would be very interested...

Thanks

---

### Post by ronparent on 2009-04-09
It is unlikely that you unknowingly have a raid setup, but just to verify what your setup is, try clicking the down box with sda (upper right hand corner in your gparted image). If another unformatted drive shows, then we would have to figure out whether it was a raid0 or raid1. If it is a raid, gparted on the desktop distribution cannot handle it and procceding would destroy the array (I mean wipe data, no physical harm to the disk). Also lets see what the "sudo sfdisk -l" output is in a live cd terminal?

---

### Post by xi_Slick_ix on 2009-04-10
This is what sudo sfdisk -l gave...

[[IMG]http://i113.photobucket.com/albums/n225/halobravesfan06/Linux/th_sudo_sfdisk_-l.jpg[/IMG]](http://s113.photobucket.com/albums/n225/halobravesfan06/Linux/?action=view&current=sudo_sfdisk_-l.jpg)

The part about the partition not starting at a cylinder boundary sounds sorta bad...

***EDIT*** Sorry posted wrong picture

---

### Post by xi_Slick_ix on 2009-04-10
Oh and definitely no unknown RAID's lurking around - the only HD showing is /dev/sda (298.09 GiB)

---

### Post by Mark Phelps on 2009-04-10
Did you do this inside Ubuntu or from the LiveCD?  If so, you should download and burn the GParted LiveCD (which you can get from Distrowatch.com).  

They keep updating it and improving it all the time.  The latest version may work better than the one in the Ubuntu distro.

---

### Post by xi_Slick_ix on 2009-04-10
This was from the Gparted Live CD - I'm still debating between regular ubuntu or the Mythbuntu for the Linux install.

---

### Post by meierfra. on 2009-04-10
Your partition table is slightly corrupt. Please post the output of 

```
sudo fdisk -lu
sudo sfdisk -d
```

Please use copy and paste instead of posting screen shot. To copy from a terminal choose "copy" in the Edit menu  or use "Ctrl+Shift+C.

---

### Post by xi_Slick_ix on 2009-04-10
Sorry About the screen shots- Will give the results as soon as I get home from class..

---

### Post by xi_Slick_ix on 2009-04-10
****Sorry for the picture ahead of time, I didn't have any luck with the copy command, and didn't have any luck copying the text into an Editor and saving it as a text file either.  Please pardon my linux ignorance.  I will try to Copy and Paste in the future - I've been posting from my laptop and haven't had any luck creating a text doc. while using the Gparted Live CD****



```

sudo fdisk -lu
sudo sfdisk -d

```
Yielded the following:


[[IMG]http://i113.photobucket.com/albums/n225/halobravesfan06/Linux/th_fdisk_sfdisk.jpg[/IMG]](http://s113.photobucket.com/albums/n225/halobravesfan06/Linux/?action=view&current=fdisk_sfdisk.jpg)

---

### Post by meierfra. on 2009-04-10
To fix the partition table, boot from a LiveCD, download the attached file "PT.txt" to your Desktop and open a terminal. Rewrite your partition table via


```

sudo sfdisk -f --no-reread /dev/sda < ~/Desktop/PT.txt

```

Do you have a Ubuntu or Linux Mint Live CD? That probably would work  best. If you are using the  gparted CD, leave out the "sudo".

---

### Post by xi_Slick_ix on 2009-04-16
Sorry for the gap in the response time - had a few tests this week.

I'm having trouble copying the PT file off of the flash drive to the root folder on the Gparted Live disk.  I'm 99% sure its due to my own ignorance.

```
cp /dev/sdb1/PT/PT.txt /root
cp: cannot stat `/dev/sdb1/PT/PT.txt': Not a directory
```

From what I can gather I'm clearly not properly (or at all) mounting the flash drive and its various subfolders / directories

I know this is outside the original scope of the thread so if I need to ask this elsewhere I understand.

Thanks again

---

### Post by meierfra. on 2009-04-16
You need to mount the flash drive first:

```
fdisk -lu
```

This should tell you the device name for the partition you need to mount (probably /dev/sdb1). Then

```
mount /dev/sdb1 /mnt
```

and 

```
sudo sfdisk -f --no-reread  -O /mnt/OldPT.sav /dev/sda < /mnt/PT.txt
 
```

(I modified the command, so that it reads "PT.txt" directly from the flash drive. I also added "-O /mnt/OldPT.sav". This backs up your current partition table to your flash drive)

---

### Post by xi_Slick_ix on 2009-04-17
In the exact version of the code u gave I got a 

```
bash: /mnt/PT.txt: No such file or directory
```

So I added a space ```
/mnt/ PT.txt
```

Which yielded a different result...

```
sfdisk: invalid option -- 0
sfdisk (util-linux-ng 2.13.1.1)Usage: sfdisk [options] devices ...
device: something like /dev/hda or /dev/sda
Useful options:
```

And then it spat out a lot of choices to use with sfdisk

Did I do something wrong?

---

### Post by meierfra. on 2009-04-17
> /dev/sdb1/PT/PT.txt

It seems I had  not looked close enough at this. Is PT.txt inside the folder PT?

Then use

```

sudo sfdisk -f --no-reread  -O /mnt/PT/OldPT.sav /dev/sda < /mnt/PT/PT.txt
```


(also the O in  -O is the letter O not the number 0)

---

### Post by xi_Slick_ix on 2009-04-17
I initially added the PT/PT.txt to fix it, but it still have me an error message - so i just pulled everything off the flast drive, formatted it, and recopied the PT.txt back onto it.

The 0 vs. 0 is a critical point, lol, and I didn't notice that myself either - lets see what happens this time..,

---

### Post by xi_Slick_ix on 2009-04-17
I Got the following message:

```
sudo sfdisk -f --no-reread  -O /mnt/PT/OldPT.sav /dev/sda < /mnt/ PT.txt

sfdisk: can specify only one device (except with -l or -s)
```

And with no gap between the ```
/mnt/PT.txt
``` I got

```
bash: /mnt/PT.txt: No such file or directory
```

So I'm not sure again.

---

### Post by meierfra. on 2009-04-17
Did you try the  code I suggested to last time:

```
sudo sfdisk -f --no-reread  -O /mnt/PT/OldPT.sav /dev/sda < /mnt/PT/PT.txt
```

Do not put a space between /mnt and /PT/PT.txt

What is the exact location of PT.txt?  Does it sit inside a folder with the name PT?

---

### Post by xi_Slick_ix on 2009-04-17
I had it in a PT subfolder, but then I just decided to format the Flashdrive in case something was causing it to mess up, so the PT.txt is the ONLY thing on the flash drive.  I believe I modified the code correctly to I was pointing directly to the PT.txt

So no, I did not use your exact code, but I can create a PT folder real quick, place the txt file in there, and try once more.

---

### Post by meierfra. on 2009-04-17
>  but I can create a PT folder real quick, place the txt file in there, and try once more.

No.That should not help.


Try

```
sudo sfdisk -f --no-reread  -O /mnt/OldPT.sav /dev/sda < /mnt/PT.txt
```


Also  did you get any error message after


```
mount /dev/sdb1 /mnt
```

What is the output of 

```
ls  /mnt
```

---

### Post by xi_Slick_ix on 2009-04-17
Your are Gonna Sh** a brick on this one.

The text file is name PT.txt (just like that, notice the case)

I tried entering the sudo sfdisk command again, got nothing

then tried ```
ls /mnt
``` which yielded

```
pt.txt
```

Once again notice the case of the letters

So I hit the up arrow, and replaced "PT.txt" with "pt.txt" 

And it started rewriting the partition table.  Now to find out if that did the trick...

---

### Post by xi_Slick_ix on 2009-04-17
I did get a ```
Warning: The partition table looks like it was made for C/H/S=*/16/63 (instead of 38913/255/63)
```

And after it displayed the new partition table I got a

```
Warning: partition 1 does not end at a cylinder boundary
```

followed by

```
Successfully wrote the new partition table

Rereading the partition table...
```

and then some stuff about if changes were made to a DOS partition

---

### Post by meierfra. on 2009-04-17
That's fine. Does gparted recognize the partition table by now?  You might have to reboot for the changes to take effect,

---

### Post by xi_Slick_ix on 2009-04-17
It still showed unallocated space - rebooting now

---

### Post by xi_Slick_ix on 2009-04-17
I lie, reopened G-Parted and success, it sees everything - Thank You So Much for all of your help!!

---

### Post by xi_Slick_ix on 2009-04-17
Ok and when going to add space to sda1:

After shrinking sda3, I am left with 109.61 GiB.  15 is going to be linux, so I'll leave that un-formatted for the moment.  the other 95 or so need to go into sda1.  

So the the 95 GiB space, do I format it as NTFS, or is there an option within sda1 to format and add unallocated space?

---

### Post by meierfra. on 2009-04-17
> G-Parted and success, it sees everything - Thank You So Much for all of your help!!

Great. 

> the 95 GiB space, do I format it as NTFS, or is there an option within sda1 to format and add unallocated space?

You can only add unallocated space to a partiton if its directly adjacent to that partition.  So if you want add the 95Gib to sda1 you will have to move  the partitions between sda1 and the 95Gib to the right.  That is doable, but it might be better to just format the 95Gib to NTFS.

---

